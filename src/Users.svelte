<script>
import { onMount } from "svelte";
import User from "./User.svelte"
 
export let showUserDetail;

export let users = [];

onMount(() => {

    setTimeout(() => {
        fetch("http://localhost:3000/users")
        .then(res => res.json())
        .then(data => {
            console.log("data: ", data);
            users = data;
        })
    }, 2000)

})


</script>

<style>

</style>

<div>

    {#each users as user}
        <div on:click={showUserDetail(user)}>
            <User {user}/>
        </div>
    {:else}
        <div>Hämtar användare</div>
    {/each}

</div>