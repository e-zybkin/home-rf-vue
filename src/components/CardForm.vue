<template>
	<form class="form" @submit.prevent>
		<WallSizeInput />
		<OpeningInputBlock/>

		<button
			class="btn"
			type="button"
		>Посчитать</button>
	</form>
</template>

<script>
	import WallSizeInput from './WallSizeInput.vue';
	import OpeningInputBlock from './OpeningInputBlock.vue';

	export default {
		components: {
			WallSizeInput,
			OpeningInputBlock,
		},
	}
</script>

<style scoped>
.form {
	display: flex;
	flex-direction: column;
	gap: 40px;
}

.btn {
	width: 300px;
	min-height: 50px;
	align-self: center;
	background-color: #4EC3E0;
	border: none;
	border-radius: 20px;
	font-size: large;
	box-shadow: 15px 15px 0 0 rgba(0, 0, 0, 0.24);
  cursor: pointer;
	transition: 0.2s all;
}

.btn:active {
	transform: scale(0.98);
	box-shadow: 3px 3px 0 0 rgba(0, 0, 0, 0.24);
}

@media screen and (max-width: 767px) {
	.btn {
		width: 200px;
	}
}
</style>
