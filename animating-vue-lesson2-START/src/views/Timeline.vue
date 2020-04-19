<template>
    <div>
        <img class="runner first" src="../assets/runner.png" alt="runner" />
        <img class="runner second" src="../assets/runner.png" alt="runner" />
         <img class="runner third" src="../assets/runner.png" alt="runner" />
    </div>
</template>

<script>
import gsap from 'gsap'
export default {
    mounted() {
    // timeline will go here
    let tl = gsap.timeline()
    tl.to('.first', { x: 700, duration: 2, ease: 'expo.out' })
    tl.to('.second', { x: 700, duration: 2, ease: 'expo.out' }, 0.5) // now with an absolute position animation to fire a half second into the timeline
    tl.to('.third', { x: 700, duration: 2, ease: 'expo.out' })
    //To set a relative position, we use a string like '-=.75' or +=.75 to set the start of one tween .75 seconds before (-=) or after (+=) the end of the animation before it
  }
    }
</script>

<style lang="scss" scoped>
.runner {
  display: block;
  height: 5em;
  width: 5em;
  margin-top: 1.5em;
}
</style>