<!----------- LOGIC ---------->
<script>
    export let name;
    export let data;
    export let icon;
</script>

<!----------- STYLE ---------->
<style>
    .data-box {
        width: 100%;
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
        display: flex;
        align-content: center;
    }

    p > img {
        margin-left: 10px;
        width: 30px;
    }

</style>

<!----------- TEMPLATE ---------->

<div class="data-box">
    <div class="data-box-header">{name}</div>
    <p>{data} {#if icon}<img src="{icon}" alt="icon">{/if}</p>
</div>
