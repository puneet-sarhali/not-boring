<script lang="ts">
	import { spring, tweened } from 'svelte/motion';

	let coords = spring(
		{ x: 0, y: 0 },
		{
			stiffness: 0.01,
			damping: 0.25
		}
	);

	let opacity = tweened(1);
	let divRef: any;
	let mouseMoveTimeout: any;

	function handleMouseMove(e) {
		clearTimeout(mouseMoveTimeout);
		const { top, left } = divRef.getBoundingClientRect();
		e.target.style.setProperty('--x', `${$coords.x}px`);
		e.target.style.setProperty('--y', `${$coords.y}px`);
		coords.set({
			x: e.clientX - left,
			y: e.clientY - top
		});
		console.log($coords.x, $coords.y);
		opacity.set(1);
		mouseMoveTimeout = setTimeout(() => {
			// After 500ms of no mouse movement, set opacity to 0 (fully transparent)
			opacity.set(0);
		}, 1000);
	}
</script>

<div
	class="relative h-[35rem] w-[18rem] rounded-md bg-repeat bg-slate-900 border border-slate-700 shadow-xl shadow-cyan-800/40"
>
	<svg
		bind:this={divRef}
		class="h-full w-full"
		style="opacity: {$opacity}"
		role="presentation"
		on:mousemove={handleMouseMove}
	>
		<defs
			><filter
				id="bbblurry-filter"
				x="-100%"
				y="-100%"
				width="400%"
				height="400%"
				filterUnits="objectBoundingBox"
				primitiveUnits="userSpaceOnUse"
				color-interpolation-filters="sRGB"
			>
				<feGaussianBlur
					stdDeviation="35"
					x="0%"
					y="0%"
					width="100%"
					height="100%"
					in="SourceGraphic"
					edgeMode="none"
					result="blur"
				/></filter
			></defs
		>
		<circle
			filter="url(#bbblurry-filter)"
			cx={$coords.x}
			cy={$coords.y}
			r={40}
			class="fill-cyan-500/40"
		/>
	</svg>
</div>
