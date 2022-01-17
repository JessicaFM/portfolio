<script>
	// styles
	import 'app.css';

	// components
	import Navbar from './components/Navbar.svelte';
    import Main from './components/Main.svelte';
</script>

<main>
	<Navbar />
	<Main />
</main>

<style lang="postcss" global>
	@tailwind base;
	@tailwind components;
	@tailwind utilities;

	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}


	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>