<!----------- STYLE ---------->
<style>
:root {
    --tangerine: #FFC900;
}

.note-container {
    padding: 0 10px;
    display: inline-flex;
    justify-content: center;
    border: solid 2px #FFC900;
    border-radius: 5px;
    font-size: 15px;
    color: var(--tangerine);
}

</style>

<!----------- TEMPLATE ---------->

<div class="note-container">
    <slot/>
</div>
