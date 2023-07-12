<script>
    // let linearMatrix = [
    //     [0, 0, 0, 0],
    //     [0, 0, 0, 0],
    //     [0, 0, 0, 0],
    // ];

    // let determinantMatrix = [ 
    //     [0, 0, 0],
    //     [0, 0, 0],
    //     [0, 0, 0],
    // ];

    // let inverseMatrix = [ 
    //     [0, 0, 0, 1, 0, 0],
    //     [0, 0, 0, 0, 1, 0],
    //     [0, 0, 0, 0, 0, 1],
    // ];

    // let mode = 0;
    let matrix = [ 
        [0, 0, 0, 1],
        [0, 0, 0, 2],
        [0, 0, 0, 3],
    ];

    let sizeOptions = [2, 3, 4, 5];
    let modeOptions = [
        "linear",
        "inverse",
        "determinant"
    ];

    let variables = [ 'z', 'y', 'x', 'w', 'v'];

    $: rows = matrix.length;
    $: columns = matrix[0]?.length;
    $: solutionsArray = matrix.map((value) => {
        return value[columns - 1];
    });
</script>

<h1 class="underline"> Matrix Operations </h1>

<div>
    <select>
        {#each sizeOptions as size}
            <option value={size}>
                {size}
            </option>
        {/each}
    </select>
    
    <select>
        {#each modeOptions as option}
            <option value={option}>
                {option}
            </option>
        {/each}
    </select>
</div>

<div class="flex flex-col">
    {#each matrix as row, i}
        <div class="flex flex-row">
        {#each row as val, j}
            {#if j >= rows}
                <span class="m-2 test-m" id={`var_${i}_${j}`}>=</span>
            {:else}
                <span class="m-2 test-m" id={`var_${i}_${j}`}>{variables[j]}:</span>
            {/if}
            <input class="border-solid border-black border-2 w-16" type="number" bind:value={val} id={`input_${i}_${j}`} />
        {/each}
        </div>
    {/each}
</div>

<div>
    <button class="border-solid border-slate-500 border-2 p-1 rounded-md hover:bg-slate-200 shadow-[inset_0_0px_4px_rgba(0,0,0,0.6)]">
        Calculate
    </button>
    
    <button class="border-solid border-slate-500 border-2 p-1 rounded-md hover:bg-slate-200 shadow-[inset_0_0px_4px_rgba(0,0,0,0.6)]" on:click={() => {console.log(matrix)}}>
        Pretty Print Internals
    </button>
</div>


