<script>
	import '$lib/styles/normalise.css';
	import '$lib/styles/index.scss';
</script>

<div class="android-homescreen snap-x">
	<slot />
</div>

<style lang="scss">
	.android-homescreen {
		background: #f8f9fa;
		aspect-ratio: 9/16;
		inline-size: auto;
		/*max-inline-size: 95vw;
		max-block-size: 80vh;*/
		/*margin: 20px;*/
		scrollbar-width: none;
		overscroll-behavior-x: contain;
		scroll-snap-align: center;
		flex-shrink: 0;
		block-size: 100%;
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
</style>
