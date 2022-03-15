<script>
	import {createEventDispatcher} from 'svelte';

	const dispath = createEventDispatcher();

	function sayHello(){
		dispath('message', {
			text: 'Hello!'
		})
	}
</script>

<button on:click={sayHello}>
	click to say hello
</button>