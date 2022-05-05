<template>
    <div id="body">
        <div id="convert-from">
            <label class="label" for="convert">Converter <b>de</b></label>
            <select name="convert" class="select-item">
                <option value="real">R$ - Real Brasileiro</option>
            </select>
        </div>
        <!--convert-from-->

        <div id="convert-to">
            <label class="label" for="converted">Converter <b>para</b></label>
                <select id="converted" class="select-item" @change="selectValue">
                    <option v-for="(n, index) in nameCurrency" :key="index">{{ n.name }}</option>
                </select>
        </div>
        <!--convert-to-->

        <div id="value-convert">
            <label class="label" for="value">Valor</label>
            <input id="input-value" type="number" name="value" placeholder="R$" >
        </div>
        <!--value-convert-->

        <div id="button-convert">
            <button id="button" @click="btnConvert">Converter</button>
        </div>
        <!--button-convert-->

        <div class="container-required">
			<div class="container-img1">
				<img src="/image/band_br.png">
				<p class="paragrafo">Real</p>
				<p id="texto-real">R$ 10.000,00</p>
			</div><!--container-img1-->

			<div class="container-vector">
				<img src="/image/vector.png">
			</div><!--container-vector-->

			<div class="container-img2">
				<img id="bandeira-moeda" src="/image/band_eua.png">
				<p class="paragrafo" id="texto-moedas">Dólar Americano</p>
				<p id="input-moedas">$ 2.000,00</p>
			</div><!--container-img2-->
		</div><!--container-required-->

    </div>
    <!--body-->
</template>

<script>
export default {
    name: "BodyConversor",
    data() {
        return {
            nameCurrency: [
                { name: "$ - Dólar Americano" },
                { name: "€ - Euro" },
                { name: "Bitcoin" }
                ]
        }
    },
    methods: {
        selectValue() {
            let select = document.querySelector('#converted').value
            let textCurrency = document.getElementById("texto-moedas")
            let bandCurrency = document.getElementById("bandeira-moeda")
            

            if(select === "$ - Dólar Americano") {
                textCurrency.innerHTML = "Dólar Americano"
                bandCurrency.src = "/image/band_eua.png"
            }

            if(select === "€ - Euro") {
                textCurrency.innerHTML = "Euro"
                bandCurrency.src = "/image/band_euro.png"
            }

            if(select === "Bitcoin") {
                textCurrency.innerHTML = "Bitcoin"
                bandCurrency.src = "/image/band_bitcoin.png"
            }

            this.btnConvert()
        
        },
        async btnConvert() {
            // Valor das moedas
            let moedas = await fetch("https://economia.awesomeapi.com.br/last/USD-BRL,EUR-BRL,BTC-BRL").then( (response) => {
                return response.json()
            })

            let dolar = moedas.USDBRL.high
            let euro = moedas.EURBRL.high
            let bitcoin = moedas.BTCBRL.high


            // Valor em reais para conversão
            let valueReal = document.querySelector("#input-value").value
            let textReal = document.querySelector("#texto-real")

            textReal.innerHTML = valueReal.toLocaleString("pt-br" , {style: "currency", currency: "BRL"})

            // Valor convertido
            let select = document.querySelector('#converted').value
            let valueConverted = document.querySelector("#input-moedas")

            if(select === "$ - Dólar Americano") {
                let valueDolar = valueReal / dolar
                valueConverted.innerHTML = valueDolar.toLocaleString("en-US" , {style: "currency", currency: "USD"})
            }

            if(select === "€ - Euro") {
                let valueEuro = valueReal / euro
                valueConverted.innerHTML = valueEuro.toLocaleString("de-DE" , {style: "currency", currency: "EUR"})
            }

            if(select === "Bitcoin") {
                let valueBit = valueReal / bitcoin
                valueConverted.innerHTML = valueBit.toLocaleString("de-DE" , {style: "currency", currency: "BTC"})
            }
        }
    }
}
</script>

<style scoped>
    #body {
        width: 400px;
        background-color: #E5E5E5;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
    }

    #body #convert-from,
    #body #convert-to,
    #body #value-convert,
    #body #button-convert {
        display: flex;
        flex-direction: column;
        width: 300px;
        margin-top: 20px;
    }

    .label {
        margin-bottom: 5px;
        color: #747474;
    }

    .select-item,
    #input-value {
        height: 40px;
        outline: none;
        font-size: 0.9rem;
        font-weight: bold;
        color: #454545;
        appearance: none;
        padding-left: 10px;
        border: 1px solid #454545;
    }

    #button {
        height: 40px;
        background-color: rgb(22, 222, 22);
        color: white;
        font-size: 1.2rem;
        border: none;
        border-radius: 30px;
        margin-bottom: 20px;
        cursor: pointer;
    }

    .container-required{
        border: 1px solid #BBBBBB;
        border-radius: 4px;
        padding-top: 12px;
        padding-bottom: 12px;
        margin-bottom: 20px;
        width: 300px;
    }

    #texto-real , #input-moedas{
        font-weight: bold;
    }

    .container-img1{
        text-align: center;
    }

    .container-vector{
        text-align: center;
        margin-top: 15px;
        margin-bottom: 15px;
    }

    .container-img2{
        text-align: center;
    }

    .paragrafo{
        color: #777777;
        font-size: 14px;
    }

</style>