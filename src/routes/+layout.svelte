<script>
	import { onMount } from 'svelte';
	/**
	 * @param {{ returnValue: boolean; }} event
	 */
	function absorbEvent(event) {
		event.returnValue = false;
	}
</script>

<div
	class="scene"
	on:touchstart={absorbEvent}
	on:touchend={absorbEvent}
	on:touchcancel={absorbEvent}
	on:touchmove={absorbEvent}
>
	<slot />
</div>

<style>
	.scene {
		width: 100%;
		height: 100%;
		position: absolute;
		inset: 0;
		background-image: linear-gradient(
			to right bottom,
			#c6ff00,
			#d7f200,
			#e4e500,
			#efd700,
			#f7ca00,
			#fdb50d,
			#ff9f1e,
			#ff8a2d,
			#ff6549,
			#ff3272,
			#ff00a5,
			#ff00df
		);
		background-attachment: fixed;
	}
</style>
