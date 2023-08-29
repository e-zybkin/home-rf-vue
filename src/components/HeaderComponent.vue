<template>
  <header>
    <div class="logo"></div>
    <h1 class="title">Калькулятор ПГП</h1>
  </header>
</template>

<script></script>

<style scoped>
header {
  padding: 20px;
  line-height: 1.5;
  display: flex;
  align-items: center;
  gap: 30px;
  border: 1px solid #2f444e;
  border-radius: 20px;
  box-shadow: 15px 15px 0 0 #2f444e;
  margin-bottom: 50px;
}

.logo {
  width: 30px;
  height: 30px;
  border-radius: 50%;
  background-color: #8bc540;
}

@media (max-width: 767px) {
  header {
    gap: 15px;
  }
  .logo {
    width: 20px;
    height: 20px;
  }
  .title {
    font-size: medium;
  }
}
</style>
