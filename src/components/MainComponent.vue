<template>
	<main>
    <CardForm  />
		<CalcResult />
  </main>
</template>

<script setup>
import CardForm from './CardForm.vue'
import CalcResult from './CalcResult.vue'
</script>

<style scoped>
main {
	display: flex;
	flex-direction: column;
}

</style>