<script>
	import { tweened, spring } from 'svelte/motion';
	import { onMount } from 'svelte';
	import SvgOrbit from './svg-orbit.svelte';

	const numStars = 100;

	const stars = Array.from({ length: numStars }, () => {
		return {
			tweened: tweened({ x: 0, y: 0, angle: 0 }),
			seed: Math.random() * 10 + 1
		};
	});

	const orbitRadius = 50;

	function updateStarPositions() {
		const currentTime = performance.now();
		const angle_slow = (currentTime / 10000) % (2 * Math.PI);
		const angle_fast = (currentTime / 8000) % (2 * Math.PI);
		let angle = 0;
		stars.forEach((star, i) => {
			Math.floor(star.seed) % 2 == 0 ? (angle = angle_slow) : (angle = angle_fast);
			star.tweened.set({
				x: orbitRadius * star.seed * Math.cos(angle + (i * 2 * Math.PI) / numStars) + 400,
				y: orbitRadius * star.seed * Math.sin(angle + (i * 2 * Math.PI) / numStars) + 200,
				angle
			});
		});

		requestAnimationFrame(updateStarPositions);
	}

	onMount(() => {
		updateStarPositions();
	});
</script>

<svg class="border border-cyan-300/10" width="800" height="400" xmlns="http://www.w3.org/2000/svg">
	{#each stars as star}
		<SvgOrbit {star} />
	{/each}
</svg>
