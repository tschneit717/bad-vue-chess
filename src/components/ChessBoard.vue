<script lang="ts">
    import GridSquare from './GridSquare.vue';
    import ChessPiece from './ChessPiece.vue';
    import { ALPHABET, STARTING_POSITIONS } from './../constants'

    type Grid = {
        square: String,
        color: String
    }[]
    export default {

        data() {
            return {
                grid: [] as Grid
            };
        },
        components: { GridSquare, ChessPiece },
        computed: {
            buildGrid() {
                const grid = []
                for (let i = 1; i < 9; i++) {
                    const row = []
                    for (let j = 1; j < 9; j++) {
                        let temp = {
                            square: `${ALPHABET.charAt(j - 1)}${i}`,
                            color: (j + i) % 2 == 0 ? 'white' : 'black',
                            piece: STARTING_POSITIONS[i][j]
                        }
                        row.push(temp)
                    }
                    grid.push(row)
                }
                return grid
            }
        }
    }
</script>

<template>
    <div v-for="j in buildGrid" class="chessboard-row">
        <GridSquare :color="i.color" v-for="i in j">
            <!-- {{ i.square }} -->
            <ChessPiece :color="i.piece.color"></ChessPiece>
        </GridSquare>
    </div>
</template>

<style scoped>
    button {
    font-weight: bold;
    }

    .chessboard-row {
        display: grid;
        grid-template-columns: repeat(8, 50px);
        height: 50px;

    }
</style>