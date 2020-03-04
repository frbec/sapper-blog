<script>
	import Aside from "../components/Aside.svelte"
	import Footer from "../components/Footer.svelte";
</script>

<style>
	main {
		display: flex;
		flex-direction: column-reverse;
		justify-content: center;
		margin: auto;
		padding: 2em 1em;
	}

	@media (min-width: 800px) {
		main {
			flex-direction: row;
			max-width: 56em;
		}
	}
</style>
<main>
	<Aside />
	<section>
		<slot></slot>
	</section>
</main>
<Footer />