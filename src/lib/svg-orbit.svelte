<script lang="ts">
	export let star: any;
	let { tweened } = star;
</script>

<circle
	cx={$tweened.x}
	cy={$tweened.y}
	r={Math.random() * 1.5 + 0.5}
	class="fill-cyan-500 animate-pulse"
	opacity="0.5"
/>
