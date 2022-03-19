<script>
	import { Meta, Template, Story } from '@storybook/addon-svelte-csf';
	import Page from './Page.svelte';
</script>

<Meta title="Example/Page" component={Page} />

<Template let:args>
	<Page />
</Template>

<Story name="Primary" />
