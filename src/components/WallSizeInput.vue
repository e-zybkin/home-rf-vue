<template>
	<div class="block">
		<h2 class="title">Стена</h2>
		<img
			src="../assets/wall.jpg"
			alt="Великие художества"
			class="picture"
		/>
		
		<div class="inputBlock">
			<p class="inputBox">
				<label>
					Укажите общую длину стены - перегородки в метрах погонных (м):
				</label>
				<input
					:value="lengthSize"
					@input="$emit('update:lengthSize', Number($event.target.value))"
					type="number"
					id="lengthSize"
					name="lengthSize"
					required
					placeholder="0"
					min="1"
				>
			</p>
			
			<p class="inputBox">
				<label>
					Введите её высоту в метрах (м):
				</label>
				<input
					:value="heightSize"
					@input="$emit('update:heightSize', Number($event.target.value))"
					type="number"
					id="heightSize"
					name="heightSize"
					required
					placeholder="0"
					min="1"
				>
			</p>
		</div>
	</div>
</template>

<script>
	export default {
		props: {
			lengthSize: {
				type: Number,
			},
			heightSize: {
				type: Number,
			}
		}
	}
</script>

<style scoped>
	.block {
		width: 100%;
		min-height: 500px;
		display: flex;
		justify-content: space-between;
		align-items: center;
		border-radius: 20px;
		border: 1px solid #2f444e;
		box-shadow: 15px 15px 0 0 #8BC540;
		gap: 20px;
		padding: 50px;
		position: relative;
	}

	.title {
		position: absolute;
		top: 15px;
	}

	.inputBlock {
		display: flex;
		flex-direction: column;
		gap: 20px;
	}

	.inputBox {
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

	.picture {
		width: 60%;
		border-radius: 20px;
		box-shadow: 0 0 10px #76787A;
	}

	@media screen and (max-width: 1023px) {
		.block {
			flex-direction: column;
			padding: 20px;
		}

		.picture {
			margin-top: 40px;
			width: 100%;
		}
	}
</style>