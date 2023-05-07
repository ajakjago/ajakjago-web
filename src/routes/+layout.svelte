<script lang="ts">
	import { Drawer, drawerStore } from '@skeletonlabs/skeleton';
	import type { DrawerSettings } from '@skeletonlabs/skeleton';
	import { AppBar, AppShell, LightSwitch, popup } from '@skeletonlabs/skeleton';

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
	let popupclick: PopupSettings = {
		event: 'click',
		target: 'popupclick',
		placement: 'bottom'
		// Close the popup when the item is clicked
	};
	const drawerSettings: DrawerSettings = {
		position: 'right',
		width: 'w-[350px]',
		height: 'h-fit',
		padding: 'p-4',
		rounded: 'rounded-xl'
	};
	function trigger(): void {
		drawerStore.open(drawerSettings);
	}
	function close(): void {
		drawerStore.close();
	}
</script>

<!-- App Shell -->
<AppShell>
	<svelte:fragment slot="header" />
	<svelte:fragment slot="pageHeader">
		<!-- only show this in desktop mode -->
		<div class="shadow-md">
			<div class="container mx-auto">
				<AppBar
					gridColumns="grid-cols-3"
					slotDefault="place-self-center"
					slotTrail="place-content-end"
					background=""
				>
					<svelte:fragment slot="lead">
						<a href="/"
							><div class="">
								<span class="text-3xl">Ajak</span><span class="text-3xl font-semibold text-blue-700"
									>Jago</span
								>
							</div></a
						></svelte:fragment
					>

					<svelte:fragment slot="trail">
						<div class="flex flex-row items-center text-lg my-menu">
							<div>
								<a href="/" class="hover:font-bold mr-5"> Hello </a>
							</div>
							<!-- dropdown -->
							<div>
								<button class="btn hover:bg-primary-700 hover:text-white" use:popup={popupclick}>
									<span class="text-lg">Dropdown menu</span>
									<i class="fa-sharp fa-solid fa-caret-down" />
								</button>
								<div class="card p-4 w-60 shadow-xl mx-auto" data-popup="popupclick">
									<nav class="list">
										<ul>
											<li class="hover:bg-primary-500">
												<a href="/">
													<span class="w-6 text-center"><i class="fa-solid fa-home" /></span>
													<span class="ml-2">Homepage</span>
												</a>
											</li>
											<li class="hover:bg-primary-500 hover:outline-white">
												<a href="/docs/get-started">
													<span class="w-6 text-center"><i class="fa-solid fa-book" /></span>
													<span class="ml-2">Documentation</span>
												</a>
											</li>
											<li class="hover:bg-primary-500">
												<a href="/blog">
													<span class="w-6 text-center"><i class="fa-solid fa-bullhorn" /></span>
													<span class="ml-2">Blog</span>
												</a>
											</li>
											<!-- <hr class="!my-4" /> -->
										</ul>
									</nav>
									<div class="arrow bg-surface-100-800-token" />
								</div>
							</div>
							<button type="button" class="ml-2 btn variant-filled-primary text-white font-bold"
								>Contact Us</button
							>
						</div>

						<div class="visible md:hidden">
							<button
								class="btn-icon"
								on:click={() => {
									trigger();
								}}
							>
								<i class="fa-solid fa-bars" />
							</button>
						</div>
						<!-- <LightSwitch /> -->
					</svelte:fragment>
				</AppBar>
			</div>
		</div>
		<Drawer>
			<div class="w-full text-token card p-4 space-y-4">
				<nav class="list-nav text-center">
					<ul>
						<li>
							<a
								href="/"
								class="hover:font-bold mx-auto"
								on:click={() => {
									close();
								}}
							>
								Home</a
							>
						</li>
						<li>
							<a
								href="/"
								class="hover:font-bold mx-auto"
								on:click={() => {
									close();
								}}
							>
								Home</a
							>
						</li>
						<li>
							<a
								href="/"
								class="hover:font-bold mx-auto"
								on:click={() => {
									close();
								}}
							>
								Home</a
							>
						</li>
						<li>
							<a
								href="/"
								class="hover:font-bold mx-auto"
								on:click={() => {
									close();
								}}
							>
								Home</a
							>
						</li>
						<li>
							<a
								href="/"
								class="hover:font-bold mx-auto"
								on:click={() => {
									close();
								}}
							>
								Home</a
							>
						</li>
						<hr class="!my-4" />
						<!-- button close -->
						<li class="flex justify-end">
							<button
								class="btn-icon variant-filled-secondary"
								on:click={() => {
									close();
								}}
							>
								<i class="fa-solid fa-close" />
							</button>
						</li>
					</ul>
				</nav>
			</div>
		</Drawer>
	</svelte:fragment>
	<!-- Router Slot -->
	<slot />
	<!-- ---- / ---- -->
	<svelte:fragment slot="pageFooter" />
	<svelte:fragment slot="footer" />
</AppShell>

<style>
	@media only screen and (max-width: 768px) {
		.my-menu {
			display: none;
		}
	}
</style>
