<script>
import User from "./User.svelte"
 
// CALLBACK FUNKTIONEN FÖR ATT FÅNGA ETT KLICK, OBSERVERA HUR JAG SKICKAR OBJEKTET INOM ()
export let showUserDetail;

export let users = [];

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