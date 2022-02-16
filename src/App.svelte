<script>
	// styles
	import 'app.css';

	import { onMount } from "svelte"

	// components
	import Navbar from './components/Navbar.svelte';
	import Paginator from './components/Paginator.svelte';
	import Main from './components/Main.svelte';
	import About from './components/About.svelte';
	import Experience from './components/Experience.svelte';
	import Contact from './components/Contact.svelte';

	let yTop = 0
	let h
	let componentWrapper
	let maxHeight

	$: translate = translateParams(currentIndex)

	function translateParams(index) {
		let translationTop = (index * 100) + '%'
		return "translate3d(0px, " + translationTop +", 0px)"
	}

	function parseScroll() {
		yTop = componentWrapper.scrollTop
		maxHeight = ((h - 50) / 2) * (currentIndex) // here we change
		currentIndex = Math.floor(((yTop + maxHeight) / h))
	}

	function updateIndex(index) {
		console.log("current index value is: ", index);
	}

	let index = 0
	$: currentIndex = updateIndex(index)

	onMount(() => parseScroll())

</script>

<main>
	<div class="wrapper">
		<div class="content" style="--transform: { translate }">
			<Navbar />
			<Paginator bind:currentIndex={index}/>
			<div class="component">
				<div class="componentWrapper"
					bind:clientHeight={h}
					bind:this={componentWrapper}
					on:scroll={parseScroll}>
					<Main dataIndex="0" />
					<About dataIndex="1" />
					<Experience dataIndex="2" />
					<Contact dataIndex="3" />
				</div>	
			</div>
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

	.component {
		height: calc(100% -  60px);
		position: relative;	
	}

	.componentWrapper {
		position: absolute;
		overflow-y: scroll;
		width: 100%;
		height: 100%;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>