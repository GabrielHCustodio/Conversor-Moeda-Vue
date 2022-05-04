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
                <select name="converted" class="select-item">
                    <option value="dolar">$ - Dólar Americano</option>
                    <option value="euro">€ - Euro</option>
                    <option value="bitcoin">Bitcoin</option>
                </select>
        </div>
        <!--convert-to-->

        <div id="value-convert">
            <label class="label" for="value">Valor</label>
            <input id="input-value" type="number" name="value" placeholder="R$">
        </div>
        <!--value-convert-->

        <div id="button-convert">
            <button id="button">Converter</button>
        </div>
        <!--button-convert-->
    </div>
    <!--body-->
</template>

<script>
export default {
    name: "BodyConversor"
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

</style>