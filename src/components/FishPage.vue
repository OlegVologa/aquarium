<script>
export default {
  data() {
    return {};
  },
  props: {
    endShow: {
      type: Boolean,
      required: true,
    },
  },
};
</script>

<template>
  <div v-if="endShow" class="form-sent d-flex flex-column text-center mb-5">
    <h2 class="form-sent__title pt-5">
      Ваша заявка успешно отправлена. Дождитесь ответа нашего специалиста для
      уточнения деталей.
    </h2>
  </div>
</template>

<style lang="scss" scoped>
.form-sent {
  min-height: 300px;
  border: 1px solid #000;
  background-image: url("../assets/form-sent.jpg");
  background-repeat: no-repeat;
  background-position: center;
  background-size: cover;
}

.form-sent__title {
  opacity: 1;
}
</style>