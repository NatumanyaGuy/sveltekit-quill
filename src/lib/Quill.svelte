<script>
	import { fade } from 'svelte/transition';
	let ComponentP = import('./_Quill.svelte').then(({ default: C }) => C);
	export let content;
	export let theme = 'snow'; //snow, bubble
</script>

{#await ComponentP}
	<slot>
		<div class={$$restProps.class || 'slot-fallback'}>
			<p>Preparing your editor.....</p>
		</div>
	</slot>
{:then Component}
	<div in:fade={{ delay: 200 }}>
		<Component bind:content {theme} class={$$restProps.class || ''} />
	</div>
{/await}

<style>
	.slot-fallback {
		min-height: 25vh;
		justify-content: center;
		text-align: center;
		align-items: center;
		justify-items: center;
		padding: 20px;
		font-size: 20px;
	}
</style>
