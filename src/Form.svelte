<script>
    export let onSubmit;

    export let first_name = "";
    export let last_name = "";
    export let email = "";

</script>

<style>

</style>

<form on:submit={onSubmit}>
    <input type="text" id="first_name" bind:value={first_name}/>
    <input type="text" id="last_name" bind:value={last_name}/>
    <input type="text" id="email" bind:value={email}/>
    <button>Spara</button>
</form>