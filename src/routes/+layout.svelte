<script>
	import Header from '$lib/header/Header.svelte';
    import '../app.css';
</script>

<Header />

<main>
	<div class="main">
		<div class="slot">
			<slot />
		</div>
	</div>
</main>

<style>
	main {
		flex: 1;
		display: flex;
		flex-direction: column;
		padding: 1rem;
		padding-top: 0;
		width: 100%;
		max-width: 1800px;
		margin: 0 auto;
		box-sizing: border-box;
	}
	.slot {
		margin-top: 10px;
	}
</style>