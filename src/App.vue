<script setup>
import IdCard from "./components/IdCard.vue";
import Random from "./components/Random.vue";
import BoxColor from "./components/BoxColor.vue";
import CreditCard from "./components/CreditCard.vue";
import Rating from "./components/Rating.vue";
import DriverCard from "./components/DriverCard.vue";
import LikeButton from "./components/LikeButton.vue";
import ClickablePicture from "./components/ClickablePicture.vue";
import Dice from "./components/Dice.vue";
import Carousel from "./components/Carousel.vue";
import NumbersTable from "./components/NumbersTable.vue";
import FaceBook from "./components/FaceBook.vue";
</script>

<template>
  <h1>Creación de componentes con Vue</h1>
  <p>Crea a conitnuación todos los componentes del ejercicio.</p>

  <h2>Iteration 1 | Component: IdCard</h2>
  <IdCard last-name="Doe" first-name="John" gender="male" :height="178" :birth="new Date('1992-07-14')" picture="https://randomuser.me/api/portraits/men/44.jpg" />
  <IdCard last-name="Delores " first-name="Obrien" gender="female" :height="172" :birth="new Date('1988-05-11')" picture="https://randomuser.me/api/portraits/women/44.jpg" />

  <h2>Iteration 2 | Component: Random</h2>
  <Random :min="1" :max="6" />
  <Random :min="1" :max="100" />

  <h2>Iteration 3 | Component: BoxColor</h2>
  <BoxColor :r="255" :g="0" :b="0" />
  <BoxColor :r="128" :g="255" :b="0" />

  <h2>Iteration 4 | Component: CreditCard</h2>
  <div class="container">
    <CreditCard type="Visa" number="0123456789018845" :expiration-month="3" :expiration-year="2021" bank="BNP" owner="Maxence Bouret" bg-color="#11aa99" color="white" />
    <CreditCard type="Master Card" number="0123456789010995" :expiration-month="3" :expiration-year="2021" bank="N26" owner="Maxence Bouret" bg-color="#eeeeee" color="#222222" />
    <CreditCard type="Visa" number="0123456789016984" :expiration-month="12" :expiration-year="2019" bank="Name of the Bank" owner="Firstname Lastname" bg-color="#ddbb55" color="white" />
  </div>

  <h2>Iteration 5 | Component: Rating</h2>
  <Rating :rate="0" />
  <Rating :rate="1.49" />
  <Rating :rate="1.5" />
  <Rating :rate="3" />
  <Rating :rate="4" />
  <Rating :rate="5" />

  <h2>Iteration 6 | Component: DriverCard</h2>
  <DriverCard
    name="Travis Kalanick"
    :rating="4.2"
    img="https://si.wsj.net/public/resources/images/BN-TY647_37gql_OR_20170621052140.jpg?width=620&height=428"
    :car="{ model: 'Toyota Corolla Altis', licensePlate: 'CO42DE' }"
  />

  <DriverCard
    name="Dara Khosrowshahi"
    :rating="4.9"
    img="https://ubernewsroomapi.10upcdn.com/wp-content/uploads/2017/09/Dara_ELT_Newsroom_1000px.jpg"
    :car="{ model: 'Audi A3', licensePlate: 'BE33ER' }"
  />

  <h2>Iteration 7 | State: LikeButton</h2>
  <div class="container">
    <LikeButton />
    <LikeButton />
  </div>

  <h2>Iteration 8: State: ClickablePicture</h2>
  <ClickablePicture img="maxence.png" img-clicked="maxence-glasses.png" />

  <h2>Iteration 9 | State: Dice</h2>
  <Dice />

  <h2>Iteration 10 | State: Carousel</h2>
  <Carousel
    :images="[
      'https://randomuser.me/api/portraits/women/1.jpg',
      'https://randomuser.me/api/portraits/men/1.jpg',
      'https://randomuser.me/api/portraits/women/2.jpg',
      'https://randomuser.me/api/portraits/men/2.jpg',
    ]"
  />

  <h2>Iteration 11 | List and Keys | NumbersTable</h2>
  <NumbersTable :limit="12" />

  <h2>Iteration 12 | List and Keys - FaceBook (Simple)</h2>
  <FaceBook />
</template>

<style scoped>
h2 {
  margin: 3rem 0;
}

div.container {
  display: flex;
}
</style>
