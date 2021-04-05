<script lang="ts">
	import Glitch from '$lib/Glitch.svelte';
</script>

<main>
	<div class="flex-wrapper">
		<div class="logo">
			<Glitch src="/images/feather-white.png" altSrc="/images/feather-white-skull.png" />
		</div>
		<div class="links">
			<a target="_blank" rel="noopener noreferrer" href="https://www.github.com/DyingAlbatross">
				Github
			</a>
			<a target="_blank" rel="noopener noreferrer" href="https://www.twitter.com/DyingAlbatross">
				Twitter
			</a>
		</div>
	</div>
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		margin: 0 auto;
	}

	.flex-wrapper {
		display: -webkit-box;
		display: -webkit-flex;
		display: -ms-flexbox;
		display: flex;
		-webkit-box-align: center;
		-webkit-align-items: center;
		-ms-flex-align: center;
		align-items: center;
		height: 95vh;
		min-height: 24em;
		-webkit-box-pack: center;
		-webkit-justify-content: center;
		-ms-flex-pack: center;
		justify-content: center;
		flex-direction: column;
		-webkit-animation: fadein 2s;
		-moz-animation: fadein 2s;
		-ms-animation: fadein 2s;
		-o-animation: fadein 2s;
		animation: fadein 2s;
	}

	.logo {
		text-align: center;
		width: 100%;
		margin-bottom: 30px;
	}

	/* .logo > img {
		width: 150px;
	} */

	.links {
		color: #666;
		font-size: 1em;
		width: 100%;
		text-align: center;
		margin-bottom: 20px;
	}

	.links a {
		color: #666;
		margin-right: 30px;
		transition: all 200ms;
	}

	.links a:hover {
		color: white;
	}
</style>
