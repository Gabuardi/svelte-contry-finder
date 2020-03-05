<!----------- LOGIC ---------->
<script>
    export let name;
    export let data;
</script>

<!----------- STYLE ---------->
<style>
    .data-box {
        border: solid 1px orange;
    }

    .data-box > * {
        padding: 10px;
    }

    .data-box-header {
        background-color: orange;
        color: #404040;
        font-weight: bold;
    }

    p {
        margin: 0;
        color: white;
    }

</style>

<!----------- TEMPLATE ---------->

<div class="data-box">
    <div class="data-box-header">{name}</div>
    <p>{data}</p>
</div>
