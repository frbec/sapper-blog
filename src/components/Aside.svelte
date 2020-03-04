<script>
	import Author from '../components/Author.svelte';
	import Profile from '../components/Profile.svelte';
</script>
<style>
	aside {
        box-sizing: border-box;
        display: flex;
        flex-direction: column;
        border: 10px solid rgb(29, 45, 56);
        border-radius: 24px;
        padding: 1em;
        margin-top: 2em;
        font-size: 0.9em;
    }
    @media (min-width: 800px) {
		aside {
			width: 16em;
            align-self: flex-start;
            flex-shrink: 0;
            margin: 0 3em 0 0;
        }
    }
</style>

<aside>
    <Author />
	<Profile /> 
</aside>