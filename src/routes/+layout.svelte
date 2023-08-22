<script lang="ts">
	import "../app.postcss";
	import { navigating } from "$app/stores";
	import Navbar from "./Navbar.svelte";
	import PageTransition from "$lib/components/PageTransition.svelte";
	import type { PageData } from "./$types";
	import { beforeNavigate } from "$app/navigation";

	export let data: PageData;

	let isAnimating: undefined | boolean;

	beforeNavigate(({ cancel }) => {
		isAnimating && cancel();
	});
</script>

<div id="faux-body" class="h-full w-full">
	<Navbar />
	<main id="content" class="h-full w-full pt-16">
		<PageTransition rerenderTrigger={data.url} bind:isAnimating>
			<div class="m-auto h-full w-full bg-white">
				<slot />
			</div>
		</PageTransition>
	</main>
</div>

<style>
</style>
