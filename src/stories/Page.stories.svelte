<script>
	import { Meta, Template, Story } from '@storybook/addon-svelte-csf';
	import Page from './Page.svelte';
</script>

<Meta title="Example/Page" component={Page} />

<Template let:args>
	<Page {...args} />
</Template>

<Story
	name="Primary"
	args={{
		publicKey: '7z7Q3UH4cMxSNDTATsQcC34rr4MVA9ydqpbeqnU4q7ba'
	}}
/>
