<script lang="ts">
    export interface ChessPiece {
        type: ChessPieceType,
        color: ChessPieceColor
    }

    enum ChessPieceType {
        Pawn = 'pawn',
        Knight = 'knight',
        Bishop = 'bishop',
        Rook = 'rook',
        Queen = 'queen',
        King = 'king',
    }

    enum ChessPieceColor {
        White = 'white',
        Black = 'black'
    }

    export default {
        props: {
            color: {
                type: String as () => ChessPieceColor,
                default: ChessPieceColor.White
            },
            piece: {
                type: String as () => ChessPieceType,
                default: ChessPieceType.Pawn
            }
        },
        created() {
            console.log(this.color)
        },
        computed: {
            icon_path() {
                return `fa-solid fa-chess-${this.piece}`
            }
        }
    }
</script>

<template>
  <div class="chess-piece" :data-color="color">
    <font-awesome-icon :icon="icon_path" />
  </div>
</template>

<style scoped>
    .chess-piece {
        width: 100%;
        height: 100%;
        display: flex;
        align-items: center;
        justify-content: center;
    }
    
    .chess-piece svg {
        height: 30px;
        cursor: pointer;
    }
    [data-color="white"] svg {
        color: #FFF;
        stroke: #000;
        stroke-width: 20px;
    }
    [data-color="black"] svg {
        color: #000;
        stroke: #FFF;
        stroke-width: 20px;
    }

</style>
