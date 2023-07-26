<script>
	import Quill from '$lib/Quill.svelte';
	let content = { html: '<p>Hello</p>', text: '' };
</script>

<div class="">
	<Quill bind:content theme="bubble" class="text-xl" />
</div>

{JSON.stringify(content)}

<svelte:head>
	<style>
		#ql.text-xl {
			font-size: 1.2rem;
		}
	</style>
</svelte:head>
