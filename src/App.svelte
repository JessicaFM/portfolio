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

	let scrollable = true;
	const wheel = (node, options) => {
		let { scrollable } = options;
		console.log("scrolling ... ")
		console.log(node);
		console.log(options);
		currentIndex += 1;
		
		const handler = e => {
			if (!scrollable) e.preventDefault();
		};
		
		node.addEventListener('wheel', handler, { passive: false });
		
		return {
			update(options) {
				scrollable = options.scrollable;
			},
			destroy() {
				node.removeEventListener('wheel', handler, { passive: false });
			}
		};
	};
	 let y = 100	
</script>

<!-- <svelte:window use:wheel={{scrollable}} /> -->
<svelte:window bind:scrollY={ y } />

<main>
	<div class="wrapper">
		<div class="content" style="--transform: { translate }">
			<Navbar />
			<Paginator />
			<Main dataIndex="0" />
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
    	/* overflow: hidden; */
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