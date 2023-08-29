<template>
	<div class="wrapper">
		<div 
			class="openingBlock"
			v-for="(input, index) in inputs"
			:key="index"	
		>
			<div class="inputBlock">
				<p class="inputBox">
					<label>
						Ширина (см):
					</label>
					<input
						:value="input.widthSize"
						@input="input.widthSize = $event.target.value"
						type="number"
						id="widthSize"
						name="widthSize"
						required
						placeholder="0"
						min="1"
					>
				</p>
				
				<p class="inputBox">
					<label>
						Высота (см):
					</label>
					<input
						:value="input.heightWallSize"
						@input="input.heightWallSize = $event.target.value"
						type="number"
						id="heightWallSize"
						name="heightWallSize"
						required
						placeholder="0"
						min="1"
					>
				</p>
			</div>

			<button type="button" class="deleteBtn" @click="deleteInput(index)">&#10006;</button>
		</div>
	</div>
	
</template>

<script>
	export default {
		props: {
			inputs: {
				type: Array,
				required: true 
			},
		},
		methods: {
			deleteInput(index) {
				this.$emit('delete', index)
			}
		}
	}
</script>

<style scoped>

.wrapper {
	display: flex;
	flex-direction: column;
	gap: 20px;
}
.openingBlock {
	display: flex;
	align-items: center;
	gap: 5px;
	box-shadow: 0 0 10px #76787A;
	padding: 10px;
	border-radius: 10px;
}

.deleteBtn {
	width: 30px;
	height: 30px;
	border: none;
	border-radius: 5px;
	box-shadow: 5px 5px 0 0 rgba(0, 0, 0, 0.24);
	cursor: pointer;
	transition: 0.2s all;
}

.deleteBtn:active {
	transform: scale(0.98);
	box-shadow: 2px 2px 0 0 rgba(0, 0, 0, 0.24);
}

.inputBlock {
	display: flex;
	gap: 20px;
}

.inputBox {
	max-width: 80px;
	display: flex;
	flex-direction: column;
	font-size: large;
	font-weight: 500;
}

.inputBox input {
	max-width: 60px;
	min-height: 30px;
	font-size: large;
	border-radius: 5px;
	border: 1px solid #76787A;
	margin-top: 10px;
}
</style>