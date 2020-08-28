<template>
    <div class="picture">
        <canvas></canvas>
    </div>
</template>

<script>
export default {
    name:'picture',
    data() {
        return {
            
        }
    },
    methods:{

    }
}
</script>
<style scoped>
.picture{
    display: block;
    width: 100%;
    height: 100%;
    padding: 25px;
    box-sizing: border-box;
}
canvas{
    display: block;
    width: 100%;
    max-width: 1280px;
    margin: 0 auto;
    box-shadow: 4px 4px 12px 0px #171717;
}
</style>