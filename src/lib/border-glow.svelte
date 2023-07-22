<script>
	import { blur } from 'svelte/transition';
</script>

<div
	class="relative h-[30rem] w-[18rem] rounded-md bg-repeat bg-gradient-to-b from-slate-800 via-slate-900 to-slate-900 border border-slate-700 shadow-xl shadow-cyan-800/40 overflow-hidden"
>
	<div
		transition:blur={{ amount: 10 }}
		class="w-48 h-80 animate-pulse bg-cyan-500/30 opacity-30 blur-xl rounded-full skew-y-12 rotate-45 transition-all"
	/>
</div>

<style>
</style>
