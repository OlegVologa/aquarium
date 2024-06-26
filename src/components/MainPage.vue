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
      slide1: {
        type: String,
        required: true,
      },
      slide2: {
        type: String,
        required: true,
      },
      slide3: {
        type: String,
        required: true,
      },
      slide4: {
        type: String,
        required: true,
      },
      courasel: {
        type: String,
        required: true,
      },
      cardBuy: {
        type: Boolean,
        required: true,
      },
      cardTab: {
        type: String,
        required: true,
      },
      cardText1: {
        type: String,
        required: true,
      },
      cardText2: {
        type: String,
        required: true,
      },
    },
  },
};
</script>

<template>
  <div class="row g-4 pb-5">
    <div
      class="col-12 col-sm-6 col-lg-4 col-xl-3"
      v-for="(cardData, id) of cardDatas"
      :key="id"
    >
      <div class="card mx-auto h-100">
        <h5 class="card-title text-center mt-3 mb-3">
          {{ cardData.cardTitle }}
        </h5>
        <div class="price d-flex justify-content-center mb-2">
          <img src="../assets/ruble.svg" class="ruble" alt="ruble" />
          <span>{{ cardData.cardPrice }}</span>
        </div>
        <div :id="cardData.courasel" class="carousel slide mb-3">
          <div class="carousel-inner">
            <div class="carousel-item active">
              <img :src="cardData.slide1" class="d-block w-100" alt="pet-1" />
            </div>
            <div class="carousel-item">
              <img :src="cardData.slide2" class="d-block w-100" alt="pet-2" />
            </div>
            <div class="carousel-item">
              <img :src="cardData.slide3" class="d-block w-100" alt="pet-3" />
            </div>
            <div class="carousel-item">
              <img :src="cardData.slide4" class="d-block w-100" alt="pet-4" />
            </div>
          </div>
          <img
            class="carousel-control-prev"
            :data-bs-target="'#' + cardData.courasel"
            data-bs-slide="prev"
            src="../assets/fish-prew.svg"
            alt="prew"
          />
          <img
            class="carousel-control-next"
            :data-bs-target="'#' + cardData.courasel"
            data-bs-slide="next"
            src="../assets/fish.svg"
            alt="next"
          />
        </div>

        <button
          class="card-buy btn mx-auto col-6 btn-outline-success"
          :class="[
            cardData.cardBuy ? 'btn-outline-danger' : 'btn-outline-success',
          ]"
          @click="toggleBuy(id)"
        >
          {{ cardData.cardBuy ? "Отменить покупку" : "Купить" }}
        </button>

        <div class="card-body">
          <nav>
            <div class="nav nav-tabs row" id="nav-tab" role="tablist">
              <button
                class="nav-link active col-6"
                id="nav-home-tab"
                data-bs-toggle="tab"
                :data-bs-target="'#nav-home' + cardData.cardTab"
                type="button"
                role="tab"
                aria-controls="nav-home"
                aria-selected="true"
              >
                Описание
              </button>
              <button
                class="nav-link col-6"
                id="nav-profile-tab"
                data-bs-toggle="tab"
                :data-bs-target="'#nav-profile' + cardData.cardTab"
                type="button"
                role="tab"
                aria-controls="nav-profile"
                aria-selected="false"
              >
                Особенности содержания
              </button>
            </div>
          </nav>
          <div class="tab-content" id="nav-tabContent">
            <div
              class="tab-pane fade show active"
              :id="'nav-home' + cardData.cardTab"
              role="tabpanel"
              aria-labelledby="nav-home-tab"
              tabindex="0"
            >
              <div class="pt-3">
                {{ cardData.cardText1 }}
              </div>
            </div>
            <div
              class="tab-pane fade"
              :id="'nav-profile' + cardData.cardTab"
              role="tabpanel"
              aria-labelledby="nav-profile-tab"
              tabindex="0"
            >
              <div class="pt-3">
                {{ cardData.cardText2 }}
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.card {
  max-width: 400px;
}

.slide {
  position: relative;
}

.carousel-control-prev,
.carousel-control-next {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
}

.tab-pane {
  text-indent: 30px;
}

.tag-pane::first-letter {
  text-transform: uppercase;
}
</style>