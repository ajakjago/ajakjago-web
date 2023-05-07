<script lang="ts">
	import { AppBar, AppShell, ListBox, ListBoxItem, popup } from '@skeletonlabs/skeleton';
	import { LightSwitch } from '@skeletonlabs/skeleton';

	let comboboxValue: string;
</script>

<AppShell>
	<div class="flex items-center justify-center h-screen">
		<div class="container p-8 space-y-8">
			<h1>Hello World</h1>
			<p>Lorem ipsum dolor sit amet consectetur adipisicing elit.</p>
			<section>
				<a class="btn variant-filled-primary" href="https://kit.svelte.dev/">SvelteKit</a>
				<a class="btn variant-filled-secondary" href="https://tailwindcss.com/">Tailwind</a>
				<a class="btn variant-filled-tertiary" href="https://github.com/">GitHub</a>
			</section>
		</div>
	</div>
</AppShell>
