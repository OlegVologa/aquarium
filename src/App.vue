<script>
import HeaderPage from './components/HeaderPage.vue'
import MainPage from './components/MainPage.vue'
import CheckOrder from './components/CheckOrder.vue'
import ContactsPage from './components/ContactsPage.vue'
import FishPage from './components/FishPage.vue'
import FooterPage from './components/FooterPage.vue'

export default {
  components: {
    HeaderPage,
    MainPage,
    CheckOrder,
    ContactsPage,
    FishPage,
    FooterPage,
  },
  methods: {
    toggle(id) {
      this.cardDatas[id].cardBuy = !this.cardDatas[id].cardBuy;
      this.endShow = false;
    },
    showEnd() {
      this.endShow = true;
    },
  },
  data() {
    return {
      endShow: false,
      cardDatas: [
        {
          id: 1,
          cardTitle: "Золотой бандит",
          cardPrice: 300,
          slide1: "/bandit-1.jpg",
          slide2: "/bandit-2.jpg",
          slide3: "/bandit-3.jpg",
          slide4: "/bandit-4.jpg",
          courasel: "couraselOne",
          cardBuy: false,
          cardTab: "tabOne",
          cardText1:
            "Эта небольшая рыбка, несмотря на кажущуюся милоту- настоящий бандит подводного мира. Всего за несколько минут она способна растерзать до четырех тигровых акул, или одного небольшого кашалота.",
          cardText2:
            "Держать исключительно в одиночку. Крышку аквариума закрывать на замок, и ключ прятать от детей!!! Кормить, подавая кусок свежего мяса при помощи кузнечных клещей.",
        },
        {
          id: 2,
          cardTitle: "Вороватый руконог",
          cardPrice: 250,
          slide1: "/rukonog-1.jpg",
          slide2: "/rukonog-2.jpg",
          slide3: "/rukonog-3.jpg",
          slide4: "/rukonog-4.jpg",
          courasel: "couraselTwo",
          cardBuy: false,
          cardTab: "tabTwo",
          cardText1:
            "Этот рукастый лупоглазик отличается маниакальной страстью к воровству наличности, а также любых красивых безделушек и просто блестящий предметов. Обчистив квартиру владельцев руконог первым делом похищает ближайший электросамокат и начинает разъезжать по городу, разбрасывая похищенную добычу из стороны в сторону.",
          cardText2:
            "Первым делом отберите у него любимый шлем и водительские права, а также ни в коем случае не пересчитывайте свою наличность у него на глазах. Хорошо прячьте деньги и дорогие сердцу украшения.",
        },
        {
          id: 3,
          cardTitle: "Сладкоголосая сирена",
          cardPrice: 600,
          slide1: "/sirena-1.jpg",
          slide2: "/sirena-2.jpg",
          slide3: "/sirena-3.jpg",
          slide4: "/sirena-4.jpg",
          courasel: "couraselThree",
          cardBuy: false,
          cardTab: "tabThree",
          cardText1:
            "Дочь морского царя больше всего на свете любит петь. Готовьтесь прикупить хороший микрофон для своей новой питомицы.",
          cardText2:
            "В помещении с сиреной всегда должна играть легкая, расслабляющая музыка, или будьте готовы к буре негодования и раздражения со стороны хрупкой красавицы с хвостом.",
        },
        {
          id: 4,
          cardTitle: "Глубоководный курильщик",
          cardPrice: 400,
          slide1: "/smoker-1.jpg",
          slide2: "/smoker-2.jpg",
          slide3: "/smoker-3.jpg",
          slide4: "/smoker-4.jpg",
          courasel: "couraselFour",
          cardBuy: false,
          cardTab: "tabFour",
          cardText1:
            "Важный морской братан, много видел, много плавал. Любит поговорить за жизнь, раскуривая очередную сигарету, и поучая проплывающих мимо глупых мальков.",
          cardText2:
            "Цепь и очки обязательны для содержания, но в комплект не входят. Также требует дополнительных расходов на табак. И... на всякий случай - поставьте огнетушитель рядом с аквариумом!",
        },
        {
          id: 5,
          cardTitle: "Рыбка-гипнотизер",
          cardPrice: 200,
          slide1: "/hypnotist-1.jpg",
          slide2: "/hypnotist-2.jpg",
          slide3: "/hypnotist-3.jpg",
          slide4: "/hypnotist-4.jpg",
          courasel: "couraselFive",
          cardBuy: false,
          cardTab: "tabFive",
          cardText1:
            "Возможно самый опасный лот нашей коллекции. Безобидная на вид рыбка является сильнейшим из известных науке гипнотизеров. Ее взгляд приковывает внимание и внушает разные (иногда совсем не безопасные) мысли.",
          cardText2:
            "Для содержания этой особи нужно иметь прежде всего развитую силу воли, или природный иммунитет к гипнозу и манипуляциям.",
        },
        {
          id: 6,
          cardTitle: "Морской шлепальщик",
          cardPrice: 400,
          slide1: "/spanker-1.jpg",
          slide2: "/spanker-2.jpg",
          slide3: "/spanker-3.jpg",
          slide4: "/spanker-4.jpg",
          courasel: "couraselSix",
          cardBuy: false,
          cardTab: "tabSix",
          cardText1:
            "Еще один странный обитатель морского дна, которого буквально нужно держать в ежевых рукавицах. Если дать ему волю, то пострадает не только владелец и его домочадцы, но может достаться на орехи даже шумным соседям.",
          cardText2:
            'Достаточно шумен. Если он не находит того, на ком можно выместить свои садистские наклонности, то сгибается пополам и резким движением шлепает сам собой. Купите ему для развлечения пару-тройку морских ежей. Чтобы было как в пословице: -"и хочется и колется".',
        },
      ],
    };
  },
  computed: {
    cardBuys: function () {
      for (let i = 0; i < this.cardDatas.length; i++) {
        if (this.cardDatas[i].cardBuy === true) {
          return  true;
        }
      }
      return false;
    },
    summBuy: function () {
      let summBuy = 0;
      for (let i = 0; i < this.cardDatas.length; i++) {
        if (this.cardDatas[i].cardBuy === true) {
          summBuy = summBuy + this.cardDatas[i].cardPrice;
        }
      }
      return summBuy;
    },
  },
}
</script>

<!-- src/App.vue -->
<template>
  <div class="container">
    <HeaderPage />
    <h1 class="text-center mb-5">
      Самые опасные, экзотические и уродливые обитатели морского дна в вашем
      аквариуме!
    </h1>
    <MainPage :cardDatas="cardDatas" @toggle="toggle" />
    <CheckOrder
      :cardDatas="cardDatas"
      :cardBuys="cardBuys"
      :summBuy="summBuy"
      @toggle="toggle"
    />
    <ContactsPage
      :cardDatas="cardDatas"
      :cardBuys="cardBuys"
      :summBuy="summBuy"
      @show="showEnd"
    />
    <FishPage :endShow="endShow" />
    <FooterPage />
  </div>
</template>

<style lang="scss">

.footer-icon {
  position: relative;
  top: -1px;
}

</style>