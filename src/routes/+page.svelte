<script>
    let grid = [[], [], []];
    let counter = 0;
    const rows = [0, 1, 2];
    const cols = [0, 1, 2];
    let turn = "X";
    function checkGameOver(grid) {
        counter = counter + 1;
        //rows
        if (
            grid[0][0] == grid[0][1] &&
            grid[0][0] == grid[0][2] &&
            grid[0][0] != undefined
        ) {
            alert(grid[0][0] + " wins");
            location.reload();
        } else if (
            grid[1][0] == grid[1][1] &&
            grid[1][0] == grid[1][2] &&
            grid[1][0] != undefined
        ) {
            alert(grid[1][0] + " wins");
            location.reload();
        } else if (
            grid[2][0] == grid[2][1] &&
            grid[2][0] == grid[2][2] &&
            grid[2][0] != undefined
        ) {
            alert(grid[2][0] + " wins");
            location.reload();
        }
        //columns
        else if (
            grid[0][0] == grid[1][0] &&
            grid[0][0] == grid[2][0] &&
            grid[0][0] != undefined
        ) {
            alert(grid[0][0] + " wins");
            location.reload();
        } else if (
            grid[0][1] == grid[1][1] &&
            grid[0][1] == grid[2][1] &&
            grid[0][1] != undefined
        ) {
            alert(grid[0][1] + " wins");
            location.reload();
        } else if (
            grid[0][2] == grid[1][2] &&
            grid[0][2] == grid[2][2] &&
            grid[0][2] != undefined
        ) {
            alert(grid[0][2] + " wins");
            location.reload();
        }
        //diagonals
        else if (
            grid[0][0] == grid[1][1] &&
            grid[0][0] == grid[2][2] &&
            grid[0][0] != undefined
        ) {
            alert(grid[0][0] + " wins");
            location.reload();
        } else if (
            grid[2][0] == grid[1][1] &&
            grid[2][0] == grid[0][2] &&
            grid[2][0] != undefined
        ) {
            alert(grid[2][0] + " wins");
            location.reload();
        } else if (counter > 8) {
            alert("Draw");
            location.reload();
        }
    }

    function isBlank(str) {
        return /^\s*$/.test(str);
    }
    function buttonFunction(event, row, col) {
        if (isBlank(event.target.innerText)) {
            event.target.innerText = turn;
            grid[row][col] = turn;
            console.log(row, col, grid[row][col], counter);
            checkGameOver(grid);
            if (turn == "X") {
                turn = "O";
            } else {
                turn = "X";
            }
        }
    }
</script>

<h1
    class="text-4xl font-extrabold absolute top-1/5 left-1/2 transform -translate-x-1/2 -translate-y-1/2 m-0"
>
    Tic-Tac-Toe
</h1>
<div
    class="absolute top-1/2 left-1/2 transform -translate-x-1/2 -translate-y-1/2 grid grid-cols-3 gap-0 m-0"
>
    {#each rows as row}
        {#each cols as col}
            <!-- svelte-ignore a11y_consider_explicit_label -->
            <button
                on:click={(e) => buttonFunction(e, row, col)}
                class="bg-white/20 backdrop-blur-md border border-white/30 text-white hover:bg-white/30 w-24 h-24 m-0 p-2 text-4xl shadow-md"
                id="{row}{col}"
            >
            </button>
        {/each}
    {/each}
</div>
