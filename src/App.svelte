<script>
	import { onMount } from "svelte";
	import Users from "./Users.svelte";
	import Form from "./Form.svelte";
	import UserDetail from "./UserDetail.svelte";

	// STATE FÖR ATT HANTERA ANVÄNDARE
	export let users = [];
	export let doUpdate = false;

	// FÖR MIN IF ROUTING
	export let showList = true;
	export let showUser = {};

	const showUserDetail = (user) => {
		console.log("user callback", user);
		showList = false;
		showUser = user;
	}

	onMount(() => {

		fetch("http://localhost:3000/users")
		.then(res => res.json())
		.then(data => {
			console.log("data: ", data);
			users = data;
		})
	})

	const onSubmit = (event) => {
        event.preventDefault();
        console.log("Formsubmit ", event.target.email.value );

        let newUser = {
            "first_name": event.target.first_name.value,
            "last_name": event.target.last_name.value,
            "email": event.target.email.value,
            "gender": "none",
            "ip_adress": "mailerdeamon"
        }

        fetch("http://localhost:3000/users", {
            method: "post",
            headers: {
                "Content-type": "application/json"
            },
            body: JSON.stringify(newUser)
        })
        .then(res => res.json())
        .then(data => {
			console.log("Success", data)
			})
        .catch(err => console.log("error", err))

		// SPARA ÄVEN NY ANVÄNDARE TILL STATE
		users.push(newUser);

		// TOGGLA DOUPDATE FÖR ATT KÖRA KEY
		doUpdate = !doUpdate
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
		<Form {onSubmit}/>
		{#key doUpdate}
			<Users {users} {showUserDetail} />
		{/key}
	{:else}
		<UserDetail {showUser} />
	{/if}

</main>

