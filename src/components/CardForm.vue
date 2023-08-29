<template>
  <form class="form" @submit.prevent>
    <WallSizeInput v-model:lengthSize="lengthSize" v-model:heightSize="heightSize" />
    <OpeningBlock :inputs="inputs" @add="addNewInput" @delete="deleteInput" />

    <button class="btn" type="submit" @click="calculateRes">Посчитать</button>
  </form>
</template>

<script>
import WallSizeInput from './WallSizeInput.vue'
import OpeningBlock from './OpeningBlock.vue'

export default {
  components: {
    WallSizeInput,
    OpeningBlock
  },
  data() {
    return {
      inputs: [{ id: 1, widthSize: 10, heightWallSize: 15 }],
      lengthSize: 0,
      heightSize: 0
    }
  },
  methods: {
    addNewInput(id, widthSize, heightWallSize) {
      const newInput = {
        id: id,
        widthSize: widthSize,
        heightWallSize: heightWallSize
      }
      this.inputs.push(newInput)
    },
    deleteInput(index) {
      this.inputs.splice(index, 1)
    },
    calculateRes() {
      console.log(this.inputs)

      const zeroInOpening =
        this.inputs.filter((item) => item.widthSize === 0 && item.heightWallSize === 0).length > 0

      const zeroInWall = this.lengthSize <= 0 || this.heightSize <= 0
      if (zeroInWall || zeroInOpening) {
        this.$emit('calculate', 500)
      } else {
        const wallArea = this.lengthSize * this.heightSize
        const openArea =
          this.inputs
            .map((item) => {
              return Number(item.widthSize) * Number(item.heightWallSize)
            })
            .reduce((a, b) => a + b, 0) / 10000

        if (wallArea <= openArea) {
          this.$emit('calculate', 600)
        } else {
          const count = Math.ceil((wallArea - openArea) / 0.3335)
          const weight = Math.ceil(count * 36)
          this.$emit('calculate', 200, count, weight)
          console.log(count)
          console.log(weight)
        }
      }
    }
  }
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
  background-color: #4ec3e0;
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
