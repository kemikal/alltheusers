<script>
 export let showUser = {};

 $: console.log("user i userDetail", showUser);

</script>

<style>

</style>

<div>
    <p>Firstname: {showUser.first_name}</p>
    <p>Lastname: {showUser.last_name}</p>
    <p>Email: {showUser.email}</p>
    <p>Gender: {showUser.gender}</p>
    <p>IP: {showUser.ip_adress}</p>
</div>

<div>
    <a href="/">Back to List</a>
</div>