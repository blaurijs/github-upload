<script>
	import Info from './Info.svelte';
	// App.svelte
	export let name;
	let count = 0;
	$: doubled = count * 2;
	$: if (count >= 10) {
		alert(`count is dangerously high!`);
		count = 9;
	}
	function handleClick(){
		count += 1;
	}
	let numbers = [1, 2, 3, 4];
	$: sum = numbers.reduce((t, n) => t + n, 0);
	function addNumber(){
		numbers.push(numbers.length + 1);
		numbers = numbers;
	}
	import Nested from './Nested.svelte';
	// Info.svelte
	const pkg = {
		name: 'svelte',
		version: 3,
		speed: 'blazing',
		website: 'https://svelte.dev'
	};
	import Login from './Login.svelte';
	import EachBlocks from './EachBlocks.svelte';
	import KeyedEachBlock from './KeyedEachBlocks.svelte';
import Await from './Await.svelte';
	let things = [
		{ id: 1, name: 'apple' },
		{ id: 2, name: 'banana' },
		{ id: 3, name: 'carrot' },
		{ id: 4, name: 'doughnut' },
		{ id: 5, name: 'egg' },
	];
	function handleThingClick() {
		things = things.slice(1);
	}
</script>

<main>
	<h1>Hello {name}!</h1>
	<p>Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn how to build Svelte apps.</p>
	<button on:click={handleClick}>
		Clicked {count} {count === 1 ? 'time' : 'times'}
	</button>
	<p>{count} doubled is {doubled}</p>
	<button on:click={addNumber}>
		Add a number
	</button>
	<p>{numbers.join(' + ')} = {sum}</p>

	<h2>Nested.svelte component with prop</h2>
	<Nested answer={42}/>

	<h2>Nested.svelte component no prop</h2>
	<Nested/>

	<h2>Info.svelte component many props</h2>
	<Info name={pkg.name} version={pkg.version} speed={pkg.speed} website={pkg.website}/>

	<h2>Login.svelte component</h2>
	<Login/>

	<h2>EachBlocks.svelte component</h2>
	<EachBlocks/>

	<h2>KeyedEachBlocks.svelte component</h2>
	<button on:click={handleThingClick}>
		Remove first thing
	</button>
	{#each things as thing}
		<KeyedEachBlock name={thing.name}/>
	{/each}

	<h2>Await.svelte component</h2>
	<Await/>
	
</main>

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