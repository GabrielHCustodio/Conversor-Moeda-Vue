<template>
    <div id="header">
        <h1>{{ titulo }}</h1>
    </div>
</template>

<script>
export default {
    name: "HeaderConversor",
    data() {
        return {
            titulo: "Conversor de moeda"
        }
    }
}
</script>

<style scoped>
    #header {
        width: 400px;
        height: 60px;
        background: rgb(59, 59, 249);
        display: flex;
        align-items: center;
        justify-content: center;
    }

    #header h1 {
        color: white;
        font-size: 1.85rem;
    }
</style>