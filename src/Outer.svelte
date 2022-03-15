<script>
	import Inner from './Inner.svelte'
	import {createEventDispatcher} from 'svelte';

	const dispath = createEventDispatcher();

	function forward(event){
		dispath('message',event.detail)
	}
</script>

<Inner on:message={forward} />