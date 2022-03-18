<script>
	import Template from './components/Template.svelte';
	let theme = "light";

	const changeTheme = () => {
		if (theme === "light") {
			theme="dark";
			document.documentElement.classList.add('dark')
		}
		else {
			theme = "light";
			document.documentElement.classList.remove('dark')
		}
	}
</script>

<div class="
	relative
	bg-slate-100 dark:bg-slate-900
	text-slate-900 dark:text-slate-100
	 w-screen h-screen  flex items-center justify-center">
	 <button type="button" class="absolute top-4 right-4 flex items-center justify-center hover:bg-slate-400 rounded-full w-10 h-10" on:click={changeTheme}>
		{#if theme === "light"}
			<i class="fa fa-sun"></i>
		{:else}
			<i class="fa fa-moon"></i>
		{/if}
	 </button>
	<Template />
</div>

<style lang="postcss" global>
	@tailwind base;
	@tailwind components;
	@tailwind utilities;
</style>