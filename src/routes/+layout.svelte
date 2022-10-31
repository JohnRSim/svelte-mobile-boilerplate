<script>
	import '$lib/styles/normalise.css';
	import '$lib/styles/index.scss';
	import { onMount, tick } from 'svelte';

	let dialog;
	let initDialog = false;
	let hideModal = false;

	onMount(async () => {});

	async function showModal() {
		dialog.showModal();
		dialog.querySelector('.snap-sentinel').scrollIntoView();

		setTimeout(() => {
			dialog.querySelector('.modal').scrollIntoView({ behavior: 'smooth' });
		}, 100);
		setTimeout(() => {
			initDialog = true;
		}, 300);
	}

	function closeModal() {
		hideModal = true;
		dialog.querySelector('.snap-sentinel').scrollIntoView({ behavior: 'smooth' });
		console.log('cli');
		initDialog = false;
		setTimeout(() => {
			dialog.close();
			hideModal = false;
		}, 300);
	}
</script>

<dialog
	class:hide={hideModal}
	bind:this={dialog}
	on:scroll={() => {
		if (initDialog && dialog.scrollTop === 0) {
			closeModal();
		}
	}}
>
	<div class="snap-sentinel" on:click={closeModal} />
	<div class="modal">
		<div class="snap-sentinel" />
		<menu>
			<button>Action 1</button>
			<button>Action 2</button>
			<button>Action 3</button>
		</menu>
		<menu>
			<button type="reset">Cancel</button>
		</menu>
	</div>
</dialog>

<div class="appUI">
	<slot />
</div>

<div class="siteWrap">
	<div class="android-homescreen snap-x">
		<section class="news">
			<header>
				<h2>News</h2>
			</header>
			<div class="card-list">
				<div class="card" />
				<div class="card" />
				<div class="card" />
				<div class="card" />
				<div class="card" />
				<div class="card" />
				<div class="card" />
				<div class="card" />
				<div class="card" />
				<div class="card" />
			</div>
		</section>

		<main>
			<div class="status-bar" />
			<div class="snap-x">
				<section>
					<div class="datetime-widget">
						<time>7:20</time>
						<date>Monday, Sept 12</date>
					</div>
					<button on:click={showModal}>testDialog</button>
				</section>
				<section>
					<nav class="app-grid">
						<div class="app" />
						<div class="app" />
						<div class="app" />
						<div class="app" />
						<div class="app" />
					</nav>
				</section>
				<section>
					<nav class="app-grid" style="align-content: start">
						<div class="app" />
						<div class="app" />
						<div class="app" />
						<div class="app" />
						<div class="app" />
						<div class="app" />
						<div class="app" />
						<div class="app" />
						<div class="app" />
						<div class="app" />
						<div class="app" />
						<div class="app" />
						<div class="app" />
						<div class="app" />
						<div class="app" />
					</nav>
				</section>
			</div>
			<footer>
				<nav>
					<div class="app" />
					<div class="app" />
					<div class="app" />
					<div class="app" />
					<div class="app" />
				</nav>
				<input type="search" placeholder="Ask Google.." />
			</footer>
		</main>
	</div>
</div>

<style lang="scss">
	.appUI {
		position: fixed;
		background: #fff;
		top: 0px;
		bottom: 0px;
		left: 0px;
		right: 0px;
		z-index: 10;
		display: none;
	}
	.siteWrap {
		display: flex;
		position: fixed;
		top: 0px;
		left: 0px;
		right: 0px;
		bottom: 0px;
	}
	.android-homescreen {
		background: #f8f9fa;
		/*aspect-ratio: 9/16;*/
		inline-size: auto;
		/*max-inline-size: 95vw;
		max-block-size: 80vh;*/
		/*margin: 20px;*/
		scrollbar-width: none;
		overscroll-behavior-x: contain;
		scroll-snap-align: center;
		flex-shrink: 0;
		block-size: 100%;
		flex: 1;
	}
	.android-homescreen::-webkit-scrollbar {
		display: none;
	}
	.snap-x {
		display: flex;
		flex-wrap: nowrap;
		overflow-x: auto;
		-ms-scroll-snap-type: x mandatory;
		scroll-snap-type: x mandatory;
	}

	.news {
		background: #f8f9fa;
		overflow-y: auto;
		display: grid;
		-webkit-animation: scroll-start 2ms;
		animation: scroll-start 2ms;
	}
	@keyframes scroll-start {
		from {
			scroll-snap-align: unset;
		}
		to {
			scroll-snap-align: center;
		}
	}
	main {
		display: grid;
		grid-template-rows: auto 1fr auto;
		scroll-snap-stop: always;
	}
	section {
		display: grid;
	}

	section,
	main {
		scroll-snap-align: center;
		flex-shrink: 0;
		inline-size: 100%;
		block-size: 100%;
	}

	header {
		padding: 1rem;
	}
	.card-list {
		display: grid;
		gap: 1px;
		grid-auto-rows: 20ch;
	}

	.card {
		background: #dee2e6;
	}
	.status-bar {
		block-size: 1.5rem;
		background: #dee2e6;
	}
	.snap-x {
		display: flex;
		flex-wrap: nowrap;
		overflow-x: auto;
		-ms-scroll-snap-type: x mandatory;
		scroll-snap-type: x mandatory;
	}
	.datetime-widget {
		display: grid;
		align-content: start;
		padding: 1rem;
	}
	.datetime-widget > time {
		font-size: 2.5rem;
		font-weight: 100;
		line-height: 0.95;
	}
	.datetime-widget > date {
		font-size: 0.75rem;
	}
	.app-grid {
		align-content: end;
	}
	nav {
		display: grid;
		grid-template-columns: repeat(5, 1fr);
		gap: 1rem;
		padding-inline: 1rem;
		padding-block: 1rem;
	}
	.app {
		aspect-ratio: 1;
		border-radius: 1e5px;
		background: #ced4da;
	}
	footer::after {
		content: '';
		background: black;
		height: 3px;
		border-radius: 3px;
		position: absolute;
		inset-block-end: 3px;
		inline-size: 30%;
		inset-inline-start: 35%;
	}
	footer {
		position: relative;
		display: grid;
	}
	input[type='search'] {
		margin: 1rem;
		background: #ced4da;
		border-radius: 1e5px;
		justify-self: stretch;
		border: 0px;
		padding-block: 0.25rem;
		padding-inline: 0.5rem;
	}

	dialog::backdrop {
		overflow: hidden;
		backdrop-filter: blur(2px);
		opacity: 0;
		background: rgba(0, 0, 0, 0.6) !important;
	}

	dialog[open]::backdrop {
		animation-name: showBackdrop;
		animation-duration: 0.6s;
		animation-delay: 0.1s;
		animation-fill-mode: forwards;
		opacity: 0;
		background: rgba(0, 0, 0, 0.6) !important;
	}
	@keyframes showBackdrop {
		0% {
			opacity: 0;
		}
		1% {
			opacity: 0;
		}
		to {
			opacity: 1;
		}
	}

	dialog[open].hide::backdrop {
		animation-name: hideBackdrop;
		animation-duration: 0.3s;
		animation-delay: 0.1s;
		animation-fill-mode: forwards;
		opacity: 1;
	}

	@keyframes hideBackdrop {
		0% {
			opacity: 1;
		}
		to {
			opacity: 0;
		}
	}

	dialog {
		pointer-events: none;
		/*
		left: 0px;
		right: 0px;
		top: auto;
		opacity: 0;
		background: #fff;
		width: auto;
		border-radius: 16px 16px 0px 0px;
		border: 0px;
		transition: bottom 0.2s;
		padding: 0px;
		position: fixed;
		will-change: transform, opacity;
		bottom: 0px;
		margin: 0px;
		width: 100%;
		max-width: unset;
		display: flex;
		overflow-y: auto;
		scroll-snap-type: y mandatory;
		max-block-size: 100vh;
		*/
		margin: 0px;
		max-width: unset;
		max-height: unset;

		overflow-y: auto;
		-ms-scroll-snap-type: y mandatory;
		scroll-snap-type: y mandatory;

		display: grid;
		grid-template-rows: 100vh auto auto;
		gap: 0px;
		padding: 0px;

		position: fixed;
		z-index: 1000;
		inset: 0;
		max-block-size: 100vh;
		scrollbar-width: none;
		left: 0px;
		right: 0px;
		top: 0px;
		bottom: 0px;
		width: 100%;
		background: transparent;
		border: 0px;
	}
	dialog::-webkit-scrollbar {
		display: none;
	}

	.modal {
		grid-row: 2;
		display: grid;
		gap: 1px;
		padding: 0;
		scroll-snap-stop: always;
		background: #fff;
		border-radius: 20px 20px 0px 0px;
	}

	.snap-sentinel {
		scroll-snap-align: start;
	}
	dialog[open] {
		/*opacity: 0;*/
		pointer-events: all;
	}

	/*dialog[open] .snap-sentinel {
		-webkit-animation: scroll-start 2ms;
		animation: scroll-start 2ms;
	}
	@keyframes scroll-start {
		from {
			scroll-snap-align: unset;
		}
		to {
			scroll-snap-align: start;
		}
	}*/
</style>
