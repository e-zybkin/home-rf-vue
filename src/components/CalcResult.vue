<template>
	<div class="resultBlock" v-if="messageCode === 200">
		<h3 class="title">На данную перегородку Вам потребуется:</h3>
		<p class="count">Пазогребных гипсовых блоков: {{this.message.count}}</p>
		<p class="allPlateWeight">Вес всех плит составит: {{this.message.weight}}</p>
	</div>
	<div class="resultBlock" v-else-if="messageCode === 500">
		Значения полей должны быть больше 0.
	</div>
	<div class="resultBlock" v-else-if="messageCode === 600">
		Введены некорректные данные.<br>Площадь проёмов больше площади стены. 
	</div>
</template>

<script>
	export default {
		props: {
			message: {
				type: Object
			},
		},
		computed: {
			messageCode() {
				return this.message.messageCode
			}
		}
	}
</script>

<style scoped>
	.resultBlock {
		margin-top: 40px;
		width: 100%;
		min-height: 200px;
		border-radius: 20px;
		border: 1px solid #2f444e;
		box-shadow: 15px 15px 0 0 #76787A;
		padding: 50px;
	}
</style>