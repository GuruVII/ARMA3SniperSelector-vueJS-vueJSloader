<template>
<div>
  <div id="loading-background" class="background-class">
  </div>
     <div class="row">
      <div class="preloader-wrapper big active" id="loading">
          <div class="spinner-layer spinner-blue-only">
              <div class="circle-clipper left">
                  <div class="circle"></div>
              </div>
              <div class="gap-patch">
                  <div class="circle"></div>
                </div>
              <div class="circle-clipper right">
                  <div class="circle"></div>
              </div>
          </div>          
      </div>
      <div id="loading-text" class="center-align">
        <p>{{loadingText}}</p>
      </div>
    </div>
</div>
</template>

<script>
export default {
  name: 'LoadingScreen',
  props: ["currentlyLoadingProp"],
  data(){
    return{loadingTextArray: ["Annexing Sweden...", "Calculating the fate of the galaxy...", "Weighing Hunter...", "Meassuring Hella's gayness...", "Looking into the future...", "Aligning the planets...", "1 + 1 = ?...", "Poking Mobinet...", "LOLing at Karton...", "Going potty..."],
    loadingText: "starting selection..."
  }
  },
  methods: {
    loadingScreenTextCrawl: function(){
      let max = Math.floor((Math.random() * 5) + 4); //determines max number of loading text that will be displayed 
      for (let i = 0; i <= max; i++){
        let interval = Math.floor((Math.random() * 2000) + 500);
        ( (i) =>{
          setTimeout(() => {
          let selectedText = Math.floor((Math.random() * this.loadingTextArray.length))
          this.loadingText = this.loadingTextArray[selectedText]
          this.loadingTextArray.splice(selectedText, 1)
          if ( i == max){
            this.$emit("loadingComplete")
          }
        }, interval * i)
        })(i);

      };


    }
  },
  mounted(){
    this.loadingScreenTextCrawl()
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

#loading {
    position: fixed;
    z-index: 1000;
    margin-left: auto;
    margin-right: auto;
    width: 90px;
    height: 90px;
    right: 0;
    left: 0;
    margin-top: 20%;

}
#loading-text{
    position: fixed;
    z-index: 1000;
    margin-top: 30%;
    right: 0;
    left: 0;
}

#loading-background.background-class {
    background-color: #1a1a1a;
    width: 100%;
    height: 100%;
    position: fixed;
    left: 0;
    top: 100;
    z-index: 100;
    opacity: 0.3;
    filter: alpha(opacity=50);
    /* For IE8 and earlier */
    transition: opacity 1s ease-out;
    -ms-transition: opacity 1s ease-out;
    -moz-transition: opacity 1s ease-out;
    -webkit-transition: opacity 1s ease-out;
}

</style>
