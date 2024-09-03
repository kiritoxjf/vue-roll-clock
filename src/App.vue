<script setup>
import Digit from './components/Digit.vue'
const props = defineProps({
	value: {
		type: String,
		default: '12:34:56'
	},
	background: {
		type: String,
		default: '#007175'
	}
})
</script>
<template>
	<div class="vue-roll-clock" :style="`background-color: ${props.background}`">
		<Digit :type="2" :digit="Number(props.value[0])" :background="props.background" />
		<Digit :digit="Number(props.value[1])" :background="props.background" />
		<span>:</span>
		<Digit
			:type="1"
			:digit="Number(props.value[3])"
			:background="props.background" />
		<Digit :digit="Number(props.value[4])" :background="props.background" />
		<span>:</span>
		<Digit
			:type="1"
			:digit="Number(props.value[6])"
			:background="props.background" />
		<Digit :digit="Number(props.value[7])" :background="props.background" />
	</div>
</template>
<style scoped>
.vue-roll-clock {
	display: flex;
	flex-direction: row;
	align-items: center;
	justify-content: center;
	height: 100%;
	width: 100%;
	font-weight: bold;
	color: inherit;
}
</style>
