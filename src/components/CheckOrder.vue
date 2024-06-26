<script>
export default {
  methods: {
    toggleBuy(id) {
      this.$emit("toggle", id);
    },
  },
  emits: ["toggle"],
  data() {
    return {};
  },
  props: {
    cardDatas: {
      id: {
        type: Number,
        required: true,
      },
      cardTitle: {
        type: String,
        required: true,
      },
      cardPrice: {
        type: Number,
        required: true,
      },
      cardBuy: {
        type: Boolean,
        required: true,
      },
    },
    cardBuys: {
      type: Boolean,
      required: true,
    },
    summBuy: {
      type: Number,
      required: true,
    },
  },
};
</script>

<template>
  <div v-if="cardBuys" class="px-sm-5 mb-5">
    <h3 class="mb-4 text-center">Проверьте ваш заказ</h3>
    <div v-for="(cardData, id) of cardDatas" :key="id" class="spisok mb-4">
      <div
        v-if="cardData.cardBuy"
        class="d-flex justify-content-between align-items-center flex-wrap row-gap-3"
      >
        <h5 class="col-7 col-sm-5 ms-lg-5">{{ cardData.cardTitle }}</h5>
        <img
          src="../assets/ruble.svg"
          class="ruble col-1 me-3 mb-1"
          alt="ruble"
        />
        <h5 class="col-2 col-sm-1">{{ cardData.cardPrice }}</h5>
        <button
          class="card-buy btn btn-outline-danger mx-auto col-12 col-sm-4 col-lg-3 mb-4"
          @click="toggleBuy(id)"
        >
          {{ "Отменить покупку" }}
        </button>
      </div>
    </div>
    <div class="d-flex justify-content-center align-items-center mb-4">
      <h4 class="me-3">Итого:</h4>
      <img src="../assets/ruble.svg" class="ruble me-3 mb-1" alt="ruble" />
      <h4>{{ summBuy }}</h4>
    </div>
  </div>
</template>

<style lang="scss" scoped>
</style>