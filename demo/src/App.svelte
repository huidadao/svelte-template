<script>
	import ContactCard from './ContactCard.svelte'

	let name = 'Max'
	let title = ''
	let image = ''
	let description = ''
	let formState = 'empty'

	let createdContacts = []

	function addContact(event){
		if(
			name.trim().length == 0 || title.trim().length == 0 || image.trim().length == 0 || description.trim().length == 0
		){
			formState = 'invalid'
			return
		}
		createdContacts = [...createdContacts, {
			id: Math.random(),
			name: name, 
			title: title, 
			image: image, 
			description: description
		}]
		formState = 'done'
	}

	function deleteFirst(){
		createdContacts = createdContacts.slice(1)
	}

	function deleteLast(){
		createdContacts = createdContacts.slice(0, -1)
	}
</script>

<form id="form" on:submit|preventDefault={addContact} >
	<div class="form-control">
		<label for="userName">User Name</label>
		<input type="text" bind:value={name} id="username">
	</div>
	<div class="form-control">
		<label for="jobTitle">Job Title</label>
		<input type="text" bind:value={title} id="jobTitle">
	</div>
	<div class="form-control">
		<label for="image">Image URL</label>
		<input type="text" bind:value={image} id="image">
	</div>
	<div class="form-control">
		<label for="desc">Description</label>
		<input type="text" bind:value={description} id="desc">
	</div>
	<button type="submit">Add Contact Card</button>
</form>

<button on:click={(event) => createdContacts = createdContacts.slice(1)}>
	Delete First
</button>
<button on:click={() => deleteLast()}>Delete Last</button>

{#if formState === 'invalid'}
	<p>Invalid input.</p>
{:else}
	<p>Please enter name some data and hit the button!</p>
{/if}

{#each createdContacts as contact, i (contact.id)}
	<h2>#{i+1}</h2>
	<ContactCard {contact} />
{:else}
	<p>Please start adding some contacts, we found none!</p>
{/each}


<style>
	#form{
		width: 30rem;
		max-width: 100%;
		margin: 1rem 0;
	}
	button{
		padding: 10px;
		background-color: darkgrey;
	}
</style>
