<script>
    import Bolus from './Bolus.svelte';
    let glycemie = 150; // mg/dl
    let glucides = 0; // g
    let facteurCorrection = 45; // Facteur de correction mg/dl/U
    let objectif = 150; // Objectif glycémique mg/dl
    let rapportInsulineGlucides = 10; // g / U
    let correction = 0; // U
    let repas = 0; // U

    function calculeCorrection() {
        correction = ((glycemie - objectif) / facteurCorrection);
    }

    function calculeRepas() {
        repas = glucides / rapportInsulineGlucides;
    }
</script>

<style>
.settings {
    font-size: 50%;
}
</style>

<span>
    <label for="glycemie">Glycémie</label>
    <input type="number" min="40" max="500" bind:value={glycemie} on:change={calculeCorrection} id="glycemie">
    <span>mg/dl</span>
</span>

<span>
    <label for="glucides">Glucides</label>
    <input type="number" min="0" max="100" bind:value={glucides} on:change={calculeRepas} id="glucides">
    <span>g</span>
</span>

<Bolus
    name="Correction"
    value={correction}
/>

<Bolus
    name="Bolus repas"
    value={repas}
/>

<Bolus
    name="Bolus total"
    value={correction + repas}
/>

<div class="settings">
    <span>
        <label for="facteurCorrection">Facteur de correction</label>
        <input type="number" min="1" max="200" bind:value={facteurCorrection} on:change={calculeCorrection} id="facteurCorrection">
        <span>mg/dl/U</span>
    </span>

    <span>
        <label for="objectif">Objectif glycémique</label>
        <input type="number" min="80" max="200" bind:value={objectif} on:change={calculeCorrection} id ="objectif">
        <span>mg/dl</span>
    </span>

    <span>
        <label for="rapport">Rapport glucides / insuline</label>
        <input type="number" min="1" max="100" bind:value={rapportInsulineGlucides} on:change={calculeRepas} id="rapport">
        <span>g/U</span>
    </span>
</div>
