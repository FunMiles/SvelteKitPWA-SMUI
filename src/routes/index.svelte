<script context="module" lang="ts">
	export const prerender = true;
</script>

<script lang="ts">
	import Button, { Label, Icon } from '@smui/button';
	import TopAppBar, { Row, Section, Title } from '@smui/top-app-bar';
	import IconButton from '@smui/icon-button';
	import Counter from '$lib/Counter/index.svelte';
	let clicked = 0;
	let secondaryColor = false;
	let prominent = false;
	let dense = false;
</script>

<svelte:head>
	<title>Home</title>
</svelte:head>

<section>
	<div class="top-app-bar-container">
		<TopAppBar
			variant="static"
			{prominent}
			{dense}
			color={secondaryColor ? 'secondary' : 'primary'}
		>
			<Row>
				<Section>
					<IconButton class="material-icons">menu</IconButton>
					<Title>Flex Static</Title>
				</Section>
				<Section align="end" toolbar>
					<IconButton class="material-icons" aria-label="Download">file_download</IconButton>
					<IconButton class="material-icons" aria-label="Print this page">print</IconButton>
					<IconButton class="material-icons" aria-label="Bookmark this page">bookmark</IconButton>
				</Section>
			</Row>
		</TopAppBar>
		<h1>
			<div class="welcome">
				<picture>
					<source srcset="svelte-welcome.webp" type="image/webp" />
					<img src="svelte-welcome.png" alt="Welcome" />
				</picture>
			</div>

			to your new<br />SvelteKit app
		</h1>

		<h2>
			try editing <strong>src/routes/index.svelte</strong>
		</h2>
		<Button on:click={() => clicked++}>
			<Icon class="material-icons">thumb_up</Icon>
			<Label>Click Me</Label>
		</Button>
		<p>{clicked}</p>
		<!-- <Counter /> -->
	</div>
</section>

<style>
	section {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		flex: 1;
	}

	h1 {
		width: 100%;
	}

	.welcome {
		position: relative;
		width: 100%;
		height: 0;
		padding: 0 0 calc(100% * 495 / 2048) 0;
	}

	.welcome img {
		position: absolute;
		width: 100%;
		height: 100%;
		top: 0;
		display: block;
	}
	.top-app-bar-container {
		max-width: 480px;
		width: 100%;
		height: 320px;
		border: 1px solid var(--mdc-theme-text-hint-on-background, rgba(0, 0, 0, 0.1));
		margin: 0 18px 18px 0;
		background-color: var(--mdc-theme-background, #fff);

		overflow: auto;
		display: inline-block;
	}

	@media (max-width: 480px) {
		.top-app-bar-container {
			margin-right: 0;
		}
	}
</style>
