<script>
import { useVuelidate } from "@vuelidate/core"
import { required, email, helpers, minLength } from "@vuelidate/validators"
const alpha = helpers.regex(/^[a-zA-Zа-яёА-ЯЁ]*$/);
export default {
  setup() {
    return { v$: useVuelidate() };
  },
  data() {
    return {
      userName: "",
      userPhone: "",
      userEmail: "",
      selectCheckbox: false,
    };
  },
  methods: {
    registerUser() {
      console.log("Регистрация прошла успешно!");
      console.log(this.userName);
      console.log(this.userPhone);
      console.log(this.userEmail);
      this.v$.reset;
      for (let i = 0; i < this.cardDatas.length; i++) {
        if (this.cardDatas[i].cardBuy === true) {
          this.cardDatas[i].cardBuy = false;
        }
      }
      return (this.cardBuys = false);
    },
    openEnd() {
      this.$emit("show");
    },
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
  validations() {
    return {
      userName: { required, alpha, minLength: minLength(3) },
      userPhone: { required },
      userEmail: { required, email },
    };
  },
  emits: ["show"],
  disabledBtn() {
    let per =
      !this.v$.userName.$invalid &&
      !this.v$.userPhone.$invalid &&
      !this.v$.userEmail.$invalid &&
      this.selectCheckbox;
    return per;
  },
  computed: {
    disabledBtn() {
      let per =
        !this.v$.userName.$invalid &&
        !this.v$.userPhone.$invalid &&
        !this.v$.userEmail.$invalid &&
        this.selectCheckbox;
      return per;
    },
  },
};
</script>

<template>
  <form
    v-if="cardBuys"
    action="../php/index.php"
    method="post"
    enctype="multipart/form-data"
    class="form-data form__body mb-5 px-sm-5"
    id="form"
    @submit.prevent="registerUser"
    novalidate
  >
    <h3 class="mb-4 text-center">
      Оставьте ваши контакты и наш специалист свяжется с вами в самое ближайшее
      время
    </h3>
    <div class="col-sm-8 col-lg-6 mx-auto mb-4">
      <input
        @blur="v$.userName.$touch()"
        v-model="userName"
        class="form-control mb-2"
        :class="{ 'is-invalid reqInput': v$.userName.$error }"
        name="NAME"
        type="text"
        placeholder="Ваше имя"
        id="userName"
        autocomplete="off"
      />
      <div v-if="this.userName === ''" class="invalid-feedback">
        Пожалуйста, выберите имя пользователя.
      </div>
      <div v-if="v$.userName.alpha.$invalid" class="invalid-feedback">
        В поле не должно содержаться цифр и других символов.
      </div>
      <div
        v-if="v$.userName.minLength.$invalid && userName != ''"
        class="invalid-feedback"
      >
        Не меньше 3 символов.
      </div>
    </div>
    <div class="col-sm-8 col-lg-6 mx-auto mb-4">
      <input
        @blur="v$.userPhone.$touch()"
        v-model="userPhone"
        class="form-control"
        :class="{ 'is-invalid reqInput': v$.userPhone.$error }"
        type="tel"
        name="PHONE"
        placeholder="Номер вашего телефона"
        id="userPhone"
        autocomplete="off"
        data-tel-input
      />
      <div v-if="!v$.userPhone.dirty" id="phoneHelp" class="form-text mt-2">
        Мы никогда никому не передадим ваш номер телефона.
      </div>
      <div
        v-if="!v$.userPhone.required && userPhone === ''"
        id="validationServerUserPhoneFeedback"
        class="invalid-feedback"
      >
        Пожалуйста, введите номер вашего телефона.
      </div>
    </div>
    <div class="col-sm-8 col-lg-6 mx-auto mb-4">
      <input
        @blur="v$.userEmail.$touch()"
        v-model="userEmail"
        class="form-control"
        :class="{ 'is-invalid reqInput': v$.userEmail.$error }"
        type="email"
        name="EMAIL"
        placeholder="Адрес электронной почты"
        id="userEmail1"
        autocomplete="off"
      />
      <div v-if="!v$.userEmail.$dirty" class="form-text">
        Пожалуйста, введите вашу почту для обратной связи.
      </div>
      <div
        v-if="!v$.userEmail.$required && !v$.userEmail.$email"
        class="invalid-feedback"
      >
        Пожалуйста, введите вашу почту для обратной связи.
      </div>
      <div v-if="!v$.userEmail.email" class="invalid-feedback">
        Поле должно быть email адресом.
      </div>
    </div>
    <div class="mb-4 form-check col-sm-8 col-lg-6 mx-auto">
      <input
        type="checkbox"
        v-model="selectCheckbox"
        class="form-check-input"
        id="formCheckbox"
      />
      <label class="form-check-label" for="formCheckbox"
        >Согласие на хранение и обработку персональных данных</label
      >
    </div>
    <button
      :disabled="!disabledBtn"
      type="submit"
      class="d-flex btn btn-primary mx-auto"
      @click="openEnd"
    >
      Отправить
    </button>
  </form>
</template>

<style lang="scss" scoped>

</style>