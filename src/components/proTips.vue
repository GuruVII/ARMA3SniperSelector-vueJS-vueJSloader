<template>
  <footer class="sticky-footer">
          <div class="container">
            <div class="row">
              <div class="col s12 center-align">
                <h6>ProTip <br>{{selectedProTip}}</h6>
              </div>
            </div>
          </div>
  </footer>
</template>

<script>
export default {
  name: 'ProTips',
  data(){
    return{
      proTips: ["#1 Best way to kill an opponent is to drive over him using a car", "#2 Need help with explosives? Ask Hawky for help, he is an expert", "#3 to fire your weapon, press fire", "#4 When in doubt, shot Hella", "#5 Try not to die", "#6 Best medicine for being injured is a bullet to the head", "#7 Don't let Hawky drive", "#8 There is no problem one cannot solves with the proper application of explosives", "#9 When Hella starts explaining things, it is alright to take a bathroom break, or clean the house, he'll still be explaining when you come back", "#10 Bored? Shot Karton", "#11 If Hella is on the stealth team, prepare for a long boring mission", "#12 Guru has an excellent record as a commander" ],
    selectedProTip: ""
    }
  },
  methods: {
    proTipSelection: function(){
      this.selectedProTip = this.proTips[Math.floor((Math.random() * this.proTips.length))]
    }
  },
  mounted(){
    this.proTipSelection()
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .sticky-footer{
    position: fixed;
    bottom: 0;
    right: 0;
    left: 0;
  }
</style>