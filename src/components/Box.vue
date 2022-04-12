<template>
  <div class='box' :style="{backgroundColor: color}" @click="handleClick(color)">
	
  </div>
</template>

<script>
export default {
  name: 'Color-Box',
  props: {
    color: String
  },
  methods: {
	handleClick(color) {
		console.log(color)
		this.$emit('onClick',color);
	}
  }
}
</script>

<style scoped>
.box{
	width: 50px;
	height: 50px;
	margin: 10px;
}
</style>
