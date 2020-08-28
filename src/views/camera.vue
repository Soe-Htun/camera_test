<template>
  <div class="camera">
      <video autoplay class="feed"></video><br>
      <button class="snap" @click="$emit('takePicture')">SNAP</button>
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: 'camera',
  data() {
    return {
      
    }
  },
  methods:{
    init(){
      if('mediaDevices' in navigator && 'getUserMedia' in navigator.mediaDevices){
            let constraints ={
                video:{
                    width:{
                        min:640,
                        ideal:1280,
                        max:1920
                    },
                    height:{
                        min:360,
                        ideal:720,
                        max:1080
                    }
                },
            }
            navigator.mediaDevices.getUserMedia({constraints: true}).then(stream => {
                console.log(constraints);
                
            const videoPlayer = document.querySelector("video");
            videoPlayer.srcObject = stream
            videoPlayer.play();
            })
        }else{
            alert("Cannot get Media Devices")
            }
        },
    
    },
    beforeMount(){
        this.init()
    }
}
</script>

<style scoped>
.camera{
  width: 100%;
  height: 100%;
  box-sizing: border-box;
}
.feed{
    width: 100%;
    margin-top: 5px;
    max-width: 1280px;
    background-color: #333;
    box-shadow: 4px 4px 12px 0px rgba(0,0,0,0.25);
  }
  .snap{
    width: 75px;
    height: 75px;
    border-radius: 50%;
    background-color: #f7d458;
    border: 1px solid #333;
    margin: 10px auto;
    opacity: 1;
  }
  .snap:hover{
    background-color: #e4b704;
  }
</style>