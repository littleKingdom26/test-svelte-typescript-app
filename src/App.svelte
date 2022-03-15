<script lang="ts">
	import Nested from './Nested.svelte'
	import Info from './Info.svelte'
	import Outer from './Outer.svelte'
	import FancyButton from "./FancyButton.svelte";



	function handleMessage(event){
		alert(event.detail.text)
	}

	const pkg ={
		name:'svelte',
		version : 3,
		speed : 'blazing',
		website : 'https://svelte.dev'
	}

	export let name: string;

	let testName = '아오우!'

	let src = 'http://ai.esmplus.com/lemon8415/0103LS/LS_089_02.jpg'
	let alt = '스타킹'
	let big = "big";

	let string = `this string contains some <strong>HTML!!!</strong>`

	let count = 0;

	$: if(count >= 10){
		alert(`count is dangerously high!`)
		count = 9
	}

	$:doubled = count*2;

	function handleClick(){
		count +=1;
	}

	function addNumber() {
		numbers = [...numbers, numbers.length + 1]
	}
	let numbers = [1,2,3,4]

	$: sum = numbers.reduce((t, n) => t + n, 0);

	let x = 4;

	let cats = [
		{id: 'J---aiyznGQ', name: 'Keyboard Cat'},
		{id: 'z_AbfPXTKms', name: 'Maru'},
		{id: 'OUtn3pvWmpg', name: 'Henri The Existential Cat'}
	];

	let m = {x:0, y: 0}
	function handleMouseOver(event){
		m.x = event.clientX;
		m.y = event.clientY;
	}

	function alertClick(){
		alert('no more alerts')
	}

	function fancyClick(){
		alert('clicked')
	}

	let a=1;
	let b=2;

	let yes = false;


	let picked = null;

	const names = ['jack', 'John', 'Mike'];
	let checkedNames = [];

</script>
<main>
	<FancyButton on:click={fancyClick}/>

	<div on:mousemove="{e => m = {x:e.clientX, y: e.clientY}}">
		The mouse position is {m.x} x {m.y}
	</div>
	<button on:click|once={alertClick}> click me </button>
	<Outer on:message={handleMessage}/>

	<input bind:value={testName}>
	<h1>Hello {testName}!</h1>

	<label>
		<input type="number" bind:value="{a}" min="0" max="10">
		<input type="range" bind:value="{a}" min="0" max="10">
	</label>

	<label>
		<input type="number" bind:value="{b}" min="0" max="10">
		<input type="range" bind:value="{b}" min="0" max="10">
	</label>

	<p>
		{a} + {b} = {a+b}
	</p>

	<label>
		<input type="checkbox" bind:checked="{yes}">
		Yes! Send me regular email spam
	</label>

	{#if yes}
		<p>Thank you. We will bombard your index and sell your personal details.</p>
	{:else}
		<p>You must opt in to countinue. If you're not paying, you're the product</p>
	{/if}
	<button disabled="{!yes}">
		Subscribe
	</button>

	<label>
		<input type="radio" value="One" bind:group={picked}>
		One
	</label>
	<br>
	<label>
		<input type="radio" value="Two" bind:group={picked}>
		Two
	</label>
	<br>
	<span>선택 : {picked}</span>

	{#each names as name, index (index)}
		<label>
			<input type="checkbox" value="{name}" bind:group="{checkedNames}">
			{name}
		</label>
	{/each}
	<br>
	<span>체크한 이름: {checkedNames}</span>


	<!--<h1>Hello {testName.toUpperCase()}!</h1>
	<p>Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn how to build Svelte apps.</p>
	{#if x > 10}
		<p>{x} is greater than 10 </p>
	{:else if 5 > x}
		<p>{x} is less then 5</p>
	{:else}
		<p>{x} is between 5 and 10</p>
	{/if}

	<ul>
		{#each cats as {id,name},i(id)}
			<li>
				<a target="_blank" href="https://www.youtube.com/watch?v={id}">{i +1}: {name}</a>
			</li>
		{/each}
	</ul>


	<Info {...pkg}/>
	<p>{numbers.join('+')} = {sum}</p>
	<button on:click="{handleClick}">
		Clicked {count} {count === 1 ? 'time':'times'}
	</button>
	<p>{count} doubled is {doubled}</p>
	<img {src} alt="{alt} star">

	<div class:big>
		빅!!!
	</div>
	<p>This is another paragraph.</p>
	<p>{@html string}</p>
	<Nested/>-->
</main>

<style lang="scss">

	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;

		div {
			width: 100%;
			height: 100%;
		}

		h1 {
			color: $primary-color;
			text-transform: uppercase;
			font-size: 4em;
			font-weight: 100;
			user-select: none;
		}
		p {
			color:purple;
			font-family: 'Comic Ssns MS',cursive;
			font-size: 2em;
		}
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>