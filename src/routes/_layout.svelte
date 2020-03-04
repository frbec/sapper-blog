<script>
	import Author from '../components/Author.svelte';
	import Profile from '../components/Profile.svelte';
</script>

<style>
	main {
		display: flex;
		justify-content: center
	}
	section {
		width: 50em;
	}
	aside {
		display: flex;
		flex-direction: column;
		max-width: 20em
	}
	.divider {
		border-left: 1px solid grey;
		margin: 2em;
	}
</style>
<main>
	<aside>
	<Author />
	<Profile />
	© Fredrik Beckius 2020
	</aside>
	<div class="divider"></div>
	<section>
		<slot></slot>
	</section>
</main>