<template>
  <div class="hello">
    <h3 class="text-center" >Choose your color</h3>
    <div class="box-container" v-if="!win">
      <ColorBox :color="data" @onClick="handleClick" v-for="(data,key) in currentData" :key="key"/>
    </div>
    <h3 class="text-center" v-if="win">You Win.</h3>
  </div>
</template>

<script>
import ColorBox from './Box.vue';
const dataset = {
  start: ['white','red'],
	firstwhite:['white','orange'],
	prevwhite:['black','red'],
  firstred: ['black','red'],
	black:['green','orange','black'],
	firstgreen:['green','orange'],
  orange:['green','orange'],
	green: [],
	red:[],
}
export default {
  name: 'HelloWorld',
  props: {
  },
  data() {
    return {
      currentData: dataset.start,
      currentKey: 'start',
      win: false,
    }
  },
  methods: {
    handleClick(color) {
      let currentKey = this.currentKey;
      if(this.currentKey !== 'black' && color === 'green'){
        this.win = true
      }
      else if ((this.currentKey === 'firstred' && color === 'red') || (this.currentKey === 'prevwhite' && color === 'red')) {
        alert("game over")
        currentKey = 'start'
      }
      else if (this.currentKey === 'start'){
        currentKey = 'first'+color;
      }
      else if (this.currentKey === 'firstwhite' && color === 'white'){
        currentKey = 'prevwhite'
      }
       else if (this.currentKey === 'black' && color === 'green'){
        currentKey = 'firstgreen'
      }
      else{
        currentKey = color
      }    
      this.currentKey = currentKey;
      this.currentData = dataset[currentKey]
    }
  },
  components: {
    ColorBox
  }
}
</script>
<style scoped>
.text-center{
  text-align: center;
}
.box-container{
  display: flex;
  justify-content: center;
}
</style>
