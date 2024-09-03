<script setup>
const props = defineProps({
	type: {
		// 0： 0-9
		// 1： 0-5
		// 2： 0-2
		type: Number,
		default: 0
	},
	digit: {
		type: Number,
		default: 0
	},
	background: {
		type: String,
		default: '#007175'
	}
})

const f = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
const s = [0, 1, 2, 3, 4, 5]
const t = [0, 1, 2]
</script>
<template>
	<div class="digit" :style="`background-color: ${props.background}`">
		<div
			class="container"
			v-if="props.type === 0"
			:style="`transform: rotateX(${-36 * props.digit}deg)`">
			<div
				class="board"
				:style="`transform: rotateX(${36 * props.digit}deg)`"></div>
			<div
				class="digit-item"
				v-for="num in f"
				:key="num"
				:style="`--i: ${num}; --j: 36; background-color: ${props.background}`">
				{{ num }}
			</div>
		</div>
		<div
			class="container"
			v-if="props.type === 1"
			:style="`transform: rotateX(${-60 * props.digit}deg)`">
			<div
				class="board"
				:style="`transform: rotateX(${60 * props.digit}deg)`"></div>
			<div
				class="digit-item"
				v-for="num in s"
				:key="num"
				:style="`--i: ${num}; --j: 60; background-color: ${props.background}`">
				{{ num }}
			</div>
		</div>
		<div
			class="container"
			v-if="props.type === 2"
			:style="`transform: rotateX(${-120 * props.digit}deg)`">
			<div
				class="board"
				:style="`transform: rotateX(${120 * props.digit}deg)`"></div>
			<div
				class="digit-item"
				v-for="num in t"
				:key="num"
				:style="`--i: ${num}; --j: 120; background-color: ${props.background}`">
				{{ num }}
			</div>
		</div>
	</div>
</template>
<style scoped>
.digit {
	display: flex;
	justify-content: center;
	align-items: center;
	width: 2rem;
	height: 2.4rem;
	font-size: inherit;
	perspective: 16rem;
	overflow: hidden;
}

.digit .container {
	display: flex;
	justify-content: center;
	align-items: center;
	width: 100%;
	height: 100%;
	transform-style: preserve-3d;
	transition: transform 0.5s linear;
}

.digit .container .board {
	position: absolute;
	width: 100%;
	height: 120%;
	background: #007175;
}
.digit .container .digit-item {
	position: absolute;
	display: flex;
	height: 2rem;
	justify-content: center;
	align-items: center;
	transform: rotateX(calc(var(--i) * var(--j) * 1deg)) translateZ(10rem);
}
</style>
