<div class="relative h-[30rem] w-[18rem] rounded-md bg-repeat bg-gradient-to-b from-slate-700 via-slate-900 to-slate-900 border border-slate-700 shadow-xl shadow-cyan-800/40" >
    <div class="absolute top-0 left-0 h-full w-full bg-gradient-to-bl from-transparent to-cyan-700 opacity-25 "></div>
    <div class="h-full w-full bg-repeat animate-lines" style="background: linear-gradient(rgba(34, 211, 238, 0.15), rgba(34, 211, 238, 0.15) 1px, transparent 1px, transparent 13px); background-size: 100% 9px;">
       <div class="p-4 pt-[22rem]">
        <h2 class="text-cyan-100 font-bold text-3xl">Stripped Lines</h2>
        <p class="text-cyan-200 text-sm mt-1">Set the starting color of a gradient using the utilities.</p>
       </div>
    </div>
</div>

<style>
    .animate-lines {
        animation: pan-overlay 25s infinite linear;
    }
    @keyframes pan-overlay {
    0% {
        background-position: 0 0;
    }
    100% {
        background-position: 0% -100%;
    }
}
</style>