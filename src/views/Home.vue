<template>
  <div>
      <camera v-on:takePicture="this.takePicture" />
      <Picture />
  </div>
</template>

<script>
// @ is an alias to /src
import camera from '@/views/camera'
import Picture from '@/views/picture'
export default {
  name: 'Home',
  components:{
    camera,
    Picture
  },
  data() {
    return {
      
    }
  },
  methods:{
    takePicture(){
      //console.log('data');
      let ratio = (window.innerHeight > window.innerWidth) ? 16 / 9 : 9 / 16;
      const picture = document.querySelector("canvas");
      picture.width = (window.innerWidth < 1280) ? window.innerWidth : 1280;
      picture.height = (window.innerWidth / ratio)
      const ctx= picture.getContext("2d")
      ctx.imageSmoothingEnabled = true;
      ctx.imageSmoothingQuality="high";
      ctx.drawImage(document.querySelector("video"),0,0, picture.width, picture.height)
      console.log(picture);
    }
  },
}
</script>

<style scoped>
</style>