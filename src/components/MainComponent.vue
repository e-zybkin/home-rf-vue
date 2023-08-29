<template>
	<main>
    <CardForm  @calculate="calculateRes"/>
		<CalcResult :message="message"/>
  </main>
</template>

<script>
import CardForm from './CardForm.vue'
import CalcResult from './CalcResult.vue'

export default {
	components: {
		CardForm,
		CalcResult,
	},
	data() {
		return {
			message: {
				messageCode: '',
				count: 0,
				weight: 0,
			},
		}
	},
	methods: {
		calculateRes(code, count, weight) {
			this.message.messageCode = code;
			this.message.count = count;
			this.message.weight = weight;
		},
	}
}
</script>

<style scoped>
main {
	display: flex;
	flex-direction: column;
}

</style>