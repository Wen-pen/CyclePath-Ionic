<script>
	import router from "page"
	import Home from "../src/Routes/Start.svelte"
	import Timer from "../src/Routes/Timer.svelte"
	import LastTime from "../src/Routes/LastTime.svelte"
	let page
	let params

	router("/", () => (page = Home))
	router("/start", () => (page = Timer))
	router("/last", () => (page = LastTime))

	router.start()
</script>

<svelte:component this="{page}" params="{params}" />
