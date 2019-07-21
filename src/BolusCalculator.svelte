<script>
    import Bolus from './Bolus.svelte';
    import Setting from './Setting.svelte';
    let glycemie = 150; // mg/dl
    let glucides = 0; // g
    let facteurCorrection = 45; // Facteur de correction mg/dl/U
    let objectif = 150; // Objectif glycémique mg/dl
    let rapportGlucidesInsuline = 10; // g / U

    $: correction = (glycemie - objectif) / facteurCorrection; // U
    $: repas = glucides / rapportGlucidesInsuline; // U
</script>

<style>
.settings {
    font-size: 50%;
}
</style>

<span>
    <label for="glycemie">Glycémie</label>
    <input type="number" min="40" max="500" bind:value={glycemie} id="glycemie">
    <span>mg/dl</span>
</span>

<span>
    <label for="glucides">Glucides</label>
    <input type="number" min="0" max="100" bind:value={glucides} id="glucides">
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
    <Setting
        name="Facteur de correction"
        min="1"
        max="200"
        bind:value={facteurCorrection}
        unit="mg/dl/U"
    />

    <Setting
        name="Objectif glycémique"
        min="80"
        max="200"
        bind:value={objectif}
        unit="mg/dl"
    />

    <Setting
        name="Rapport glucides / insuline"
        min="1"
        max="100"
        bind:value={rapportGlucidesInsuline}
        unit="g/U"
    />
</div>
