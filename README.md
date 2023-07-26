# sveltekit-quill

`sveltekit-quill` is an unofficial wrapper for Quill.js, designed specifically for seamless integration with SvelteKit projects. This library allows you to easily add rich text editing capabilities to your SvelteKit applications with the flexibility to customize the editor's appearance and behavior to suit your needs.

### Features

- Based on Quill.js: Benefit from the robustness and reliability of Quill.js, a popular and battle-tested rich text editor library.
- SvelteKit Compatibility: Integrates effortlessly with SvelteKit, providing optimal performance and a smooth developer experience.

### Installation

You can install the Sveltekit-Quill component library using npm:

```
npm install sveltekit-quill
```

### Usage

```html
<script>
	import Quill from '$lib/Quill.svelte'; //Import Quill Component
	let content = { html: '<p>Hello</p>', text: 'Hello' }; //Initialize Rich Text Editor Content
</script>

<Quill bind:content theme="bubble" class="text-xl">
	<p>Loading...</p>
</Quill>

<!----View Editor Content--->
<pre>{JSON.stringify(content)}</pre>
```

### Props

The following are props you can pass to the Quill component
| Prop | Description |
| --- | ----------- |
| Loading Slot | Set your own loading indicator for the editor as it loads. (sveltekit-quill uses {#await} for rendering ) |
| theme | Theme of the editor (`snow` or `bubble`) |
| class| pass css classes to editor |

### Important

#### Using custom classes for styling

This is a dirty way to achieve this but it works, adding read Quill documentation to TODO. Feel free to clone or contribute and improve this library.

1. Use a CSS framework such as TailwindCSS for styling ...OR
2. If using plain css; pass classes via <svelte:head> and target editor container id `#ql`

```html
<svelte:head>
	<style>
		#ql.text-xl {
			font-size: 1.2rem;
		}
	</style>
</svelte:head>
```
