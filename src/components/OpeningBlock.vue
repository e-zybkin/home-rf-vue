<template>
  <div class="block">
    <h2 class="title">Проёмы</h2>

    <OpeningInputList :inputs="inputs" @delete="deleteInput" />

    <button type="button" class="btn" @click="addNewInput(Date.now(), 0, 0)">Добавить проём</button>

    <img src="../assets/open.jpg" alt="Великие художества: часть 2" class="picture" />
  </div>
</template>

<script>
import OpeningInputList from './OpeningInputList.vue'
export default {
  props: {
    inputs: {
      type: Array,
      required: true
    }
  },
  components: {
    OpeningInputList
  },
  methods: {
    addNewInput(id, widthSize, heightWallSize) {
      this.$emit('add', id, widthSize, heightWallSize)
    },
    deleteInput(index) {
      this.$emit('delete', index)
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
  box-shadow: 15px 15px 0 0 #8bc540;
  gap: 20px;
  padding: 50px;
  position: relative;
}

.title {
  position: absolute;
  top: 15px;
}

.picture {
  width: 40%;
  border-radius: 20px;
  box-shadow: 0 0 10px #76787a;
  object-fit: cover;
  object-position: center;
}

.btn {
  width: 200px;
  height: 50px;
  border: none;
  border-radius: 10px;
  background-color: #4ec3e0;
  font-size: medium;
  box-shadow: 7px 7px 0 0 rgba(0, 0, 0, 0.24);
  cursor: pointer;
  transition: 0.2s all;
}

.btn:active {
  transform: scale(0.98);
  box-shadow: 3px 3px 0 0 rgba(0, 0, 0, 0.24);
}

@media screen and (max-width: 1023px) {
  .block {
    flex-direction: column-reverse;
    padding: 20px;
  }

  .picture {
    margin-top: 40px;
    width: 90%;
  }

  .btn {
    width: 180px;
  }
}
</style>
