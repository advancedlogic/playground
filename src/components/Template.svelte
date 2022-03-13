<div class="relative bg-slate-800 w-2/3 rounded-lg p-4 flex flex-col items-center justify-start">
    <div class="
        w-full
        flex-none flex flex-row items-center space-x-2
        text-slate-400">
        <i class="flex-none fa fa-magnifying-glass"></i>
        <input 
            type="text" 
            placeholder="   type your query here..."
            bind:value={input}
            class="
                p-2
                bg-slate-800
                outline-none
                flex-auto">
    <div class="form-check">
        <input class="form-check-input 
            appearance-none 
            h-4 w-4 
            border border-red-300 
            rounded-full
            bg-red-600 checked:bg-green-800 
            checked:border-green-600 
            focus:outline-none 
            transition duration-200 
            mt-1 
            align-top 
            bg-no-repeat 
            bg-center 
            bg-contain 
            float-left 
            mr-2 
            cursor-pointer" type="checkbox" on:click={enableSemantic}>
        <label class="text-slate-400" for="">
            {#if semantic}
            Semantic Search Enabled
            {:else}
            Semantic Search Disabled
            {/if}
        </label>
    </div>
    </div>
    {#if semantic}
    <div class="w-full flex items-center space-x-2 flex-wrap">
        {#each tokens as token, i}
            {#if map[token]}
                {#each map[token] as tag}
                <div class="px-0 py-1">
                    <div class="px-2 py-1 cursor-pointer hover:bg-{colors[i]}-600 flex flex-row items-center space-x-2 rounded-lg {bgColors(i)} {textColors(i)} text-xs">
                        <div class="">{tag}</div>
                        <button type="button" class="rounded-full hover:bg-{colors[i]}-800 w-4 h-4">
                            <i class="fa fa-x cursor-pointer"></i>
                        </button>
                    </div>
                </div>
                {/each}
            {/if}
        {/each}
    </div>
    {/if}
</div>
<script>
    let input = "";
    let semantic = false;
    let map = {
        "virus": ["microbiology", "medicine", "computer science"],
        "bank": ["finance", "economy", "geography"],
        "ball": ["sport", "anatomy"],
        "soccer": ["sport"]
    }

    const enableSemantic = () => {
        console.log("Template:enableSemantic:semantic", semantic);
        semantic = !semantic;
    }

    let ntoken = 0;
    let colors = ["red", "blue", "green", "yellow", "orange", "purple", "brown", "slate", "gray"]

    $: tokens = input.split(" ");
    const bgColors = (i) => `bg-${colors[i]}-800`;
    const textColors = (i) => `text-${colors[i]}-400`;
</script>