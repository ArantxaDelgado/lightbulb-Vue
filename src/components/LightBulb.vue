<template>
  <div v-if="cargas > 0" @click="clicked" class="bulb bulb-off">
        <p> {{ cargas }} </p>
    </div>
    <div v-else class="bulb bulb-on">
    </div>
</template>

<script>
export default {
  props: ["charges"],
  emits: ['switchedOn'],
  data() {
    return {
      cargas: this.charges,
    }
  },
  methods: {
    clicked() {
        this.cargas--;

        //Cuando cargas == 0 hay que emitir un custom event que le hemos llamado 'switchedOn'.
        if (this.cargas == 0) {
            this.$emit('switchedOn')
        }
    },
  }
}
</script>

<style scoped>
p {
  font-size: 1.5rem;
  font-weight: 700;
}

.bulb {
  display: flex;
  justify-content: center;
  align-items: center;
  cursor: pointer;
  user-select: none;
}

.bulb-off {
  width: 265px;
  height: 400px;
  background: url("lightoff.png") no-repeat;
  margin: auto;
}

.bulb-on {
  width: 265px;
  height: 400px;
  background: url("lighton.png") no-repeat;
  margin: auto;
}
</style>