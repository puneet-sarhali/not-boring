<script>
	import { tweened } from 'svelte/motion';
	import { quadIn } from 'svelte/easing';

	const buttonWidth = tweened(120, {
		duration: 200,
		easing: quadIn
	});

	const svgOpacity = tweened(0);
</script>

<div class="flex items-center group">
	<!-- svelte-ignore a11y-mouse-events-have-key-events -->
	<button
		class="animate-button relative text-left"
		on:mouseover={() => {
			buttonWidth.set(150);
			svgOpacity.set(100);
		}}
		on:mouseout={() => {
			buttonWidth.set(120);
			svgOpacity.set(0);
		}}
		style="--button-width: {$buttonWidth}px"
	>
		<span class="text-left">Hover me</span>
	</button>
	<svg
		class="w-6 h-6 fill-white opacity-0 group-hover:opacity-100 group-hover:-translate-x-10 transition-all duration-300"
		xmlns="http://www.w3.org/2000/svg"
		width="1024"
		height="1024"
		viewBox="0 0 1024 1024"
	>
		<path
			d="M869 487.8L491.2 159.9c-2.9-2.5-6.6-3.9-10.5-3.9h-88.5c-7.4 0-10.8 9.2-5.2 14l350.2 304H152c-4.4 0-8 3.6-8 8v60c0 4.4 3.6 8 8 8h585.1L386.9 854c-5.6 4.9-2.2 14 5.2 14h91.5c1.9 0 3.8-.7 5.2-2L869 536.2a32.07 32.07 0 0 0 0-48.4z"
		/></svg
	>
</div>

<style>
	.animate-button {
		padding: 10px 20px;
		background-color: #3498db;
		color: #fff;
		border: none;
		border-radius: 5px;
		cursor: pointer;
		width: var(--button-width);
		transition: width 0.1s ease; /* Add the CSS transition property */
	}
</style>
