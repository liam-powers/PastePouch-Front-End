<script>
	import { onMount } from 'svelte';

	let userid = '';
	let pasteinfo = '';

	function addPaste() {
		//TODO: Paste logic with localhost
	}

	let pasteCount = 'fetching...';
	let userCount = 'fetching...';
	onMount(async () => {
		const getPasteCountRes = await fetch(`http://localhost:8080/getPasteCount`);
		let pasteCountObj = await getPasteCountRes.json();
		pasteCount = pasteCountObj[0].count;

		const getUserCountRes = await fetch(`http://localhost:8080/getUserCount`);
		let userCountObj = await getUserCountRes.json();
		userCount = userCountObj[0].count;
	});

	let count = 0;
	function incrementCount() {
		count++;
	}
</script>

<h1>Welcome to SvelteKit</h1>
<p>Visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to read the documentation</p>

<h1>Enter your paste information here</h1>
<!-- <class="flex flex-col items-center"> -->
<input bind:value={userid} placeholder="enter your userid" />
<input bind:value={pasteinfo} placeholder="enter your paste information" />
<button on:click={addPaste}>Click to Add Paste!</button>

<div>Paste count: {pasteCount}</div>
<div>User count: {userCount}</div>

<button on:click={incrementCount}>Click to increment this vague count!</button>
<div>Count: {count}</div>
<!-- </> -->
