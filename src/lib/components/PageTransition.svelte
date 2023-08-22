<script lang="ts">
	import { page, navigating } from "$app/stores";
	import { beforeNavigate } from "$app/navigation";
	import { fly } from "svelte/transition";

	export let duration = 400;
	export let rerenderTrigger = "";
	export let isAnimating = false;
</script>

{#key rerenderTrigger}
	<div
		class="h-full w-full"
		in:fly|global={{ delay: duration, duration, x: "-100%" }}
		out:fly|global={{ duration, x: "100%" }}
		on:introstart={() => (isAnimating = true)}
		on:introend={() => (isAnimating = false)}
		on:outrostart={() => (isAnimating = true)}
		on:outroend={() => (isAnimating = false)}
	>
		<slot />
	</div>
{/key}

<!-- <div class="pancake">
	{#key data.url}
		<div
			in:fly={{ y: -200, duration: 300, delay: 300 }}
			out:fly={{ y: 200, duration: 300 }}
		>
			<slot />
		</div>
	{/key}
</div> -->

<!-- <style>
	.pancake {
		display: grid;
		grid-template-columns: 1fr;
		overflow: hidden; /* prevent from going outside element */
	}

	.pancake > * {
		grid-area: 1 / 1; /* pancake */
	}
</style> -->
