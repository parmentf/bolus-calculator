<script>
    export let value = 0;
    export let name = "bolus";
</script>

<span>
    <label for="bolus">{name}</label>
    <input type="number" min="-10" max="10" value={Number(value).toFixed(1)} readonly step="0.1" id="bolus">
    <span>U</span>
</span>
