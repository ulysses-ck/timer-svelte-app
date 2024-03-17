<script>
	import Header from './Header.svelte';
	import './styles.css';
</script>

<div class="app">
	<Header />

	<main>
		<slot />
	</main>

	<footer>
		<p>
			Made with ❤️ by <a href="https://svelte.dev">Svelte</a> and
			<a href="https://kit.svelte.dev">SvelteKit</a>
		</p>
	</footer>
</div>

<style></style>
