<script>
export default {
  data() {
    return {};
  },
};
</script>

<template>
  <div
    class="d-flex flex-row flex-wrap justify-content-between align-items-center p-3"
  >
    <a class="header__logo col-4 p-2 me-2 col-md-2 col-xl-1">
      <img
        class="header__img rounded-circle"
        src="../assets/logo.png"
        alt="logo"
      />
    </a>
    <h2
      class="header__title col-7 p-2 me-2 mb-0 ps-0 text-center col-md-4 col-lg-5 col-xl-7"
    >
      Acvarium bestiaries
    </h2>
    <div
      class="header__contacts col-12 p-2 me-2 d-flex flex-column col-md-5 col-lg-4 col-xl-3"
    >
      <div class="d-flex mb-3">
        <div class="icon pe-4">
          <img src="../assets/envelope.svg" alt="email-icon" />
        </div>
        <a
          class="header__email d-flex col-10 pr-4"
          href="mailto:AcvariumBestiaries@mail.ru"
          >AcvariumBestiaries@mail.ru</a
        >
      </div>
      <div class="d-flex">
        <div class="icon pe-4">
          <img src="../assets/telephone.svg" alt="telephon-icon" />
        </div>
        <a class="header__phone d-flex col-10" href="tel:85555555555"
          >8 (555) 555-55-55</a
        >
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
a {
  color: white;
  text-decoration: none;
}

.header {
  &__img {
    width: 80px;
    height: 80px;
  }
  &__title {
    font-family: "Special Elite", sans-serif;
    text-transform: uppercase;
  }
  &__email,
  &__phone {
    position: relative;
    transition: all 0.5s ease-in;
  }
  &__email:hover,
  &__phone:hover {
    color: black;
    transform: scale(1.1);
  }
}

.icon {
  position: relative;
  bottom: 2px;
}


</style>