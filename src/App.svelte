<script>
	// styles
	import 'app.css';

	// components
	import Navbar from './components/Navbar.svelte';
	import Paginator from './components/Paginator.svelte';
    import Main from './components/Main.svelte';
	import About from './components/About.svelte';
	import Experience from './components/Experience.svelte';
	import Contact from './components/Contact.svelte';

	let currentIndex = 0 // default
	let translate = translateParams(currentIndex);
	
	function translateParams(index) {
		let translationTop = (index * 100) + '%';
		return "translate3d(0px, " + translationTop +", 0px)";
	}

	let y
	$: console.log("scrolled: ", y);	


	const layers = [0, 1, 2, 3, 4];

</script>

<svelte:window bind:scrollY={y}/>

<main>
	<div class="wrapper">
		<div class="content" style="--transform: { translate }">
			<div class="foreground">
				You have scrolled {y} pixels
			</div>
			<Navbar />
			<Paginator />
			<Main dataIndex="0" data-attr="{y}" />
			<About dataIndex="1" />
			<Experience dataIndex="2" />
			<Contact dataIndex="3" />
		</div>
	</div>
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
		width: 100%;
		height: 100%;
	}
	
	.wrapper {
		height: 100% !important;
    	height: 100%;
    	margin: 0 auto;
    	overflow: hidden;
		touch-action: none;
	}

	.content {
		float: left;
		width: 100%;
		height: 100%;
		margin: 0 auto;
		position: relative;
		transform: var(--transform);
		transition: all 1000ms ease 0s;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>