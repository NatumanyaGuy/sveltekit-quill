<script>
	// @ts-nocheck
	import { onMount } from 'svelte';
	import { quill } from 'svelte-quill';

	export let content = { html: '', text: '' };
	export let theme = 'snow';

	let toolbarOptions = {
		container: [
			[{ header: [1, 2, 3, 4, 5, 6, false] }],
			['blockquote', 'code-block', 'link', 'image'],
			['bold', 'italic', 'underline', 'strike'],
			[{ list: 'ordered' }, { list: 'ordered' }],
			[{ script: 'sub' }, { script: 'super' }],
			[{ indent: '-1' }, { indent: '+1' }],
			[{ align: [] }],
			[{ color: [] }, { background: [] }],
			['clean']
		]
	};

	let options = {
		placeholder: 'Write your story...',
		theme: theme,
		modules: {
			toolbar: toolbarOptions
		}
	};
	onMount(() => {
		//Set Initial Content
		const container = document.getElementsByClassName('ql-editor')[0];
		container.innerHTML = content.html;
	});
</script>

<svelte:head>
	{#if theme == 'bubble'}
		<link rel="stylesheet" href="//cdn.quilljs.com/1.3.6/quill.bubble.css" />
	{:else if theme == 'snow'}
		<link href="//cdn.quilljs.com/1.3.6/quill.snow.css" rel="stylesheet" />
	{/if}
</svelte:head>

<main>
	<div
		id="ql"
		class:border={theme == 'bubble'}
		class="{$$restProps.class || ''} long"
		style={$$restProps.style || ''}
		use:quill={options}
		on:text-change={(e) => {
			content = e.detail;
		}}
	/>
</main>

<style>
	.long {
		min-height: 30vh;
	}
	.border {
		border: 3px #eee solid;
	}
</style>
