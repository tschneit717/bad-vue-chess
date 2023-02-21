<script lang="ts">
    export default {
        props: {
            color: {
                type: String
            }
        },
        created() {
            console.log(this.color)
        }
    }
</script>

<template>
  <div class="square-wrapper" :data-color="color">
   <slot></slot>
  </div>
</template>

<style scoped>
    .square-wrapper {
        width: 100%;
        height: 100%;
        display: flex;
        align-items: center;
        justify-content: center;
    }

    .square-wrapper[data-color="white"] {
        background-color: white;
    }
    .square-wrapper[data-color="black"] {
        background-color: black;
    }

</style>
