<script lang="ts">
	import { page } from "$app/stores";
</script>

<nav class="bg-gray-50 w-full shadow-md fixed top-0 left-0 right-0">
	<div
		class="max-w-6xl flex justify-between items-center m-auto text-gray-800 py-2 px-8 h-16"
	>
		<h1>This is some</h1>
		<ul class="flex items-center justify-center space-x-6 uppercase">
			<li
				class:is-active={$page.route.id === "/"}
				class="tracking-wide font-semibold border border-b-2 border-b-transparent transition duration-600 hover:border-b-red-600"
			>
				<a href="/">home</a>
			</li>
			<li
				class:is-active={$page.route.id === "/about"}
				class="tracking-wide font-semibold border border-b-2 border-b-transparent transition duration-600 hover:border-b-red-600"
			>
				<a href="/about">about</a>
			</li>
			<li
				class:is-active={$page.route.id === "/info"}
				class="tracking-wide font-semibold border border-b-2 border-b-transparent transition duration-600 hover:border-b-red-600"
			>
				<a href="/info">info</a>
			</li>
		</ul>
	</div>
</nav>

<style>
	.is-active {
		@apply border border-b-2 border-b-blue-700;
	}
</style>
