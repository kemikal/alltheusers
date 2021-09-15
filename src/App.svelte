<script>
	import Users from "./Users.svelte";
	import Form from "./Form.svelte";
	import UserDetail from "./UserDetail.svelte";

	export let showList = true;
	export let showUser = {};

	const showUserDetail = (user) => {
		console.log("user callback", user);
		showList = false;
		showUser = user;
	}

</script>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}

	

</style>

<main>
	<h1>Hello All The Users!</h1>
	{#if showList === true}
		<Form />
		<Users {showUserDetail}/>
	{:else}
		<UserDetail {showUser} />
	{/if}

</main>

