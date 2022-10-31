<script>
</script>

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

<style lang="scss">
	.news {
		background: #f8f9fa;
		overflow-y: auto;
		display: grid;
		-webkit-animation: scroll-start 2ms;
		animation: scroll-start 2ms;
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
</style>
