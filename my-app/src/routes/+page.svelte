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

    // let modes = [
    //     "linear",
    //     "inverse",
    //     "determinant"
    // ]

    // let mode = 0;
    let matrix = [ 
        [0, 0, 0, 1],
        [0, 0, 0, 2],
        [0, 0, 0, 3],
    ];

    $: rows = matrix.length;
    $: columns = matrix[0]?.length;
    $: solutionsArray = matrix.map((value) => {
        return value[columns - 1];
    })
</script>

<h1> Matrix Operations </h1>
{#each matrix as row}
    <div>
    {#each row as val}
        <input value={val}>
    {/each}
    </div>
{/each}


