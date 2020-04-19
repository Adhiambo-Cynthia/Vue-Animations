GSAP and State
<template>
    <div>
    <div :style="{ width: tweenedNumber + 'px' }" class="bar">
      <span>{{ tweenedNumber.toFixed(0) }}</span>
    </div>
    </div>
</template>

<script>
import gsap from 'gsap'
export default {
    data() {
    return {
      number: 0,
      tweenedNumber: 0
    }
  },
  watch: {   //allows us to watch a reactive velue, and do things when that value changes
   number(newValue) {
      gsap.to(this.$data, { 
          duration: 1, 
	      ease: 'circ.out',
          tweenedNumber: newValue //it will animate that value by tweening it up or down to that new value, 
          //instead of just jumping abruptly to that value.
    })  
    //In this case, we don’t need GSAP to animate an element directly, we want it to animate our data,
    // because it’s our data value that is being used to widen our bar, 
    //and we’re displaying that data value within the bar
  }
},
  methods: {
    randomNumber() {
      this.number = Math.floor(Math.random() * (800 - 0))
    }
  },
  created() {
    setInterval(this.randomNumber, 1500)
  }
    }
</script>

<style scoped>
.bar {
  padding: 5px;
  background-color: #2c3e50;
  border: 1px #16c0b0 solid;
  min-width: 20px;
}
.bar span {
  color: white;
}

</style>