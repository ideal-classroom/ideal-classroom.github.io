<script>
	import { page } from '$app/stores';
	import logo from "./logo.png"
</script>

<div class="header">
	<ul>
		<li class="branding"><img height="30em" src={logo} alt="Ideal Classroom"></li>
		<li class:active={$page.url.pathname === '/'}><a href="/" preload="true">Home</a></li>
		<li class:active={$page.url.pathname === '/about'}><a href="/about" preload="true">About</a></li>
	</ul>
</div>

<style>
	.header {
		padding: 16px;
		margin: 0;
		width: 100%;
		background-color: #ffffff;
		color: #000000;
		font-size: 1em;
        font-weight: 400;
        font-family: "Poppins", sans-serif;
	}
	.active {
        font-weight: 600;
	}
	.branding {
        font-weight: 600;
		font-size: 1.1em;
		text-align: left;
		float: left;
	}
	ul {
		width: 100%;
		max-width: 1800px;
		padding: 0;
		margin: 0 auto;
		list-style-type: none;
		text-align: right;
	}
	li {
		display: inline;
		padding: 0 6px;
	}
	a {
		color: inherit;
		text-decoration: none;
	}
</style>