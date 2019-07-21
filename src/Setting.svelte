<script>
    export let name = "Setting";
    export let min = 1;
    export let max = 200;
    export let value;
    export let handleChange = () => 0;
    export let unit = "";
</script>

<span>
    <label for="setting">{name}</label>
    <input type="number" min={min} max={max} bind:value on:change={handleChange} id="setting">
    <span>{unit}</span>
</span>
