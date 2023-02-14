<script lang="ts">
	import Button from '@smui/button';
	import TopAppBar, {
		Row,
		Section,
		Title,
		AutoAdjust,
		TopAppBarComponentDev
	} from '@smui/top-app-bar';

  import IconButton from '@smui/icon-button';
 // import LoremIpsum from '$lib/LoremIpsum.svelte';

  let topAppBar: TopAppBar;
	import IconButton from '@smui/icon-button';
	import { Label, Icon } from '@smui/common';
	import { Svg } from '@smui/common/elements';
	import { mdiGithub, mdiWeb } from '@mdi/js';

	// let topAppBar: TopAppBarComponentDev;

	let lightTheme =
		typeof window === 'undefined' || window.matchMedia('(prefers-color-scheme: light)').matches;
	function switchTheme() {
		lightTheme = !lightTheme;
		let themeLink = document.head.querySelector<HTMLLinkElement>('#theme');
		if (!themeLink) {
			themeLink = document.createElement('link');
			themeLink.rel = 'stylesheet';
			themeLink.id = 'theme';
		}
		themeLink.href = `/smui${lightTheme ? '' : '-dark'}.css`;
		document.head
			.querySelector<HTMLLinkElement>('link[href="/smui-dark.css"]')
			?.insertAdjacentElement('afterend', themeLink);
	}
</script>

<!-- <TopAppBar bind:this={topAppBar} color="secondary" variant="standard">
	<Row>
		<Section>
			<Title>My App</Title>
		</Section>
		<Section align="end" toolbar>
			<IconButton aria-label="GitHub" href="https://github.com/hperrin/svelte-material-ui">
				<Icon component={Svg} viewBox="0 0 24 24">
					<path fill="currentColor" d={mdiGithub} />
				</Icon>
			</IconButton>
			<IconButton aria-label="Demo Site" href="https://sveltematerialui.com">
				<Icon component={Svg} viewBox="0 0 24 24">
					<path fill="currentColor" d={mdiWeb} />
				</Icon>
			</IconButton>
		</Section>
	</Row>
</TopAppBar> -->
<TopAppBar bind:this={topAppBar} color="secondary" variant="fixed">
  <Row>
    <Section>
      <IconButton class="material-icons">menu</IconButton>
      <Title>Fixed</Title>
    </Section>
    <Section align="end" toolbar>
      <IconButton class="material-icons" aria-label="Download"
        >file_download</IconButton
      >
      <IconButton class="material-icons" aria-label="Print this page"
        >print</IconButton
      >
      <IconButton class="material-icons" aria-label="Bookmark this page"
        >bookmark</IconButton
      >
    </Section>
  </Row>
</TopAppBar>




<AutoAdjust {topAppBar} style="display: flex; justify-content: space-between;">
	<div class="container"><slot /></div>
	<div class="container">
		<Button on:click={switchTheme}>
			<Label>{lightTheme ? 'Lights off' : 'Lights on'}</Label>
		</Button>
	</div>
</AutoAdjust>

<!-- <style>
  /* Hide everything above this component. */
  :global(#smui-app),
  :global(body),
  :global(html) {
    display: block !important;
    height: auto !important;
    width: auto !important;
    position: static !important;
  }
</style> -->



<!-- <main>
  <slot />
</main> -->

<!-- <style>
  main {
    position: relative;
    max-width: 56em;
    padding: 1em;
    margin: 0 auto;
    box-sizing: border-box;
  }
</style> -->
