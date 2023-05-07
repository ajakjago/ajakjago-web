<script lang="ts">
	import {
		AppBar,
		AppShell,
		LightSwitch,
		ListBox,
		modalStore,
		popup
	} from '@skeletonlabs/skeleton';

	import { computePosition, autoUpdate, flip, shift, offset, arrow } from '@floating-ui/dom';
	import { storePopup } from '@skeletonlabs/skeleton';
	storePopup.set({ computePosition, autoUpdate, flip, shift, offset, arrow });

	// Your selected Skeleton theme:
	import '@skeletonlabs/skeleton/themes/theme-skeleton.css';

	// This contains the bulk of Skeletons required styles:
	import '@skeletonlabs/skeleton/styles/all.css';

	// Finally, your application's global stylesheet (sometimes labeled 'app.css')
	import '../app.postcss';
	import type { PopupSettings } from '@skeletonlabs/skeleton';
	let popupHover: PopupSettings = {
		event: 'click',
		target: 'popupHover',
		placement: 'bottom'
		// Close the popup when the item is clicked
	};
</script>

<!-- App Shell -->
<AppShell>
	<svelte:fragment slot="header" />
	<svelte:fragment slot="pageHeader">
		<AppBar gridColumns="grid-cols-3" slotDefault="place-self-center" slotTrail="place-content-end">
			<svelte:fragment slot="lead"
				><a href="/"
					><div class="">
						<span class="text-3xl">Ajak</span><span class="text-3xl font-semibold text-blue-700"
							>Jago</span
						>
					</div></a
				></svelte:fragment
			>
			<div>
				<button class="btn hover:bg-blue-700 hover:text-white" use:popup={popupHover}>
					<span>Dropdown menu</span>
					<i class="fa-sharp fa-solid fa-caret-down" />
				</button>
				<div class="card p-4 w-60 shadow-xl" data-popup="popupHover">
					<nav class="list-nav">
						<ul>
							<li>
								<a href="/">
									<span class="w-6 text-center"><i class="fa-solid fa-home" /></span>
									<span>Homepage</span>
								</a>
							</li>
							<li>
								<a href="/docs/get-started">
									<span class="w-6 text-center"><i class="fa-solid fa-book" /></span>
									<span>Documentation</span>
								</a>
							</li>
							<li>
								<a href="/blog">
									<span class="w-6 text-center"><i class="fa-solid fa-bullhorn" /></span>
									<span>Blog</span>
								</a>
							</li>
							<!-- <hr class="!my-4" /> -->
						</ul>
					</nav>
					<div class="arrow bg-surface-100-800-token" />
				</div>
			</div>

			<svelte:fragment slot="trail"><LightSwitch /></svelte:fragment>
		</AppBar>
	</svelte:fragment>
	<!-- Router Slot -->
	<slot />
	<!-- ---- / ---- -->
	<svelte:fragment slot="pageFooter" />
	<svelte:fragment slot="footer" />
</AppShell>
