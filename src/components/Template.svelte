<div class="p-2 bg-slate-200 border-slate-300 shadow-lg rounded-lg w-full h-96 flex flex-row space-x-2 flex-wrap items-start justify-start">
    {#if tags.length > 0}
        <div on:keypress={(e) => e.key === 'Enter'? before(empty) : space()} 
            bind:this={pre}
            class="border-0 hover:border outline-none flex-none flex  w-{w === 0 ? '[8px]' : '[' + (8 + w) + 'px]'}" contenteditable="true" bind:textContent={empty}></div>
    {/if}
    {#each tags as tag}
        <div class="p-1 flex flex-row items-center justify-center">
            <div class="px-2 flex-none bg-red-100 border-2 border-red-800 rounded-l-full">kwd</div>
            <div class="px-2 flex-none flex text-red-100 bg-red-800 border-2 border-red-800 rounded-r-full" contenteditable="true">{tag}</div>
        </div>
    {/each}
    <input on:keypress={(e) => e.key === 'Enter'? input(query) : ''} type="text" 
    class="flex-1 pl-1 border-b border-slate-200 bg-slate-200 outline-none" bind:value={query} />
</div>
<script>
    let tags = ["test"];
    let empty = "  ";
    let query = "";
    let w = 0;
    let pre = null;

    let words = {
        "virus": ["microbiology", "medicine", "computer science"]
    }

    const space = () => {
        const text = pre.style.fontSize;
        const width = text.clientWidth;
        w = width;
    }
    const before = (item) => {
        let tmp = tags;
        tmp.unshift(item);
        tags = tmp;
        empty = "";
        w=0;
        console.log(tags)
    }
    const input = (item) => {
        let tmp = tags;
        tmp.push(item);
        query = "";
        tags = tmp;
        console.log(tags)
    }

</script>