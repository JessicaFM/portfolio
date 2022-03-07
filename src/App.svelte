<script>
	// styles
	import 'app.css';

	import { onMount } from "svelte"

	// components
	import Header from './components/Header.svelte';
	import Main from './components/Main.svelte';
	import About from './components/About.svelte';
	import Experience from './components/Experience.svelte';
	import Contact from './components/Contact.svelte';

	let yTop = 0
	let height = screen.height
	let componentWrapper
	let maxHeight

	var index = 0
	$: currentIndex = updateIndex(index)
	$: translate = translateParams(index)

	function translateParams(param) {
		console.log("translateParams", param)
		if(param > 0) {
			let translationTop = (param * 100)
			console.log("translating to: " + translationTop)
			return "translate(0px, -" + translationTop +"%)"
		} 
		return 0;
	}

	function goTo(event) {
		console.log("goint to ", event.detail.index)
		index = event.detail.index
	}

	function parseScroll() {
		yTop = componentWrapper.scrollTop
		maxHeight = ((height - 50) / 2) * (index + 1) // here we change
		console.log("yTop: " + yTop)
		console.log("maxHeight: " + maxHeight)
		console.log("h: " + height)
		currentIndex = Math.floor(((yTop + maxHeight) / height))
		console.log(screen.height)
		console.log("currentIndex: " + currentIndex)
	}

	function updateIndex(index) {
		currentIndex = index
		console.log("cc", currentIndex)
	}

	onMount(() => parseScroll())

</script>

<Header />
<main>
	<div class="wrapper">
		<div class="content">
			<div class="component" style="--transform: { translate }">
				<div class="componentWrapper"
					bind:clientHeight={height}
					bind:this={componentWrapper}
					on:scroll={parseScroll} >
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
		transition: all 1000ms ease 0s;
	}

	.component {
		height: calc(100%);
		position: relative;	
		transform: var(--transform);

	}

	.componentWrapper {
		position: absolute;
		width: 100%;
		height: 100%;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>