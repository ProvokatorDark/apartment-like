<template>
    <v-container fluid>
      <v-row dense>
        <v-col sm="6" md="4" lg="3" xl="2"
            v-for="card in cards"
            :key="card.title"
        >
          <v-card>
            <v-img
                :src="url"
                class="white--text align-end"
                gradient="to bottom, rgba(0,0,0,.1), rgba(0,0,0,.5)"
                height="200px"
            >
              <v-card-title v-text="card.attributes.title"></v-card-title>
            </v-img>
            <v-card-text>
              <div><span>Площадь: {{card.attributes.area}} {{card.attributes.unit}}</span></div>
              <div><span>Количество комнат: {{card.attributes.rooms}}</span></div>
              <div><span>Город: {{card.attributes.address.city}}</span></div>
              <div><span>Улица {{card.attributes.address.street}} дом {{card.attributes.address.house}} кв. {{card.attributes.address.room}}</span></div>
              <div><span>Агент: {{card.relationships.attributes.first_name}} {{card.relationships.attributes.middle_name}} {{card.relationships.attributes.last_name}}</span></div>
            </v-card-text>
            <v-card-actions>
              <v-spacer></v-spacer>
            <Like></Like>
            </v-card-actions>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
</template>

<script>
import axios from "axios";
import Like from "./Like";
export default {
  name: "Card",
  data: () => ({
    cards: null,
    url:"https://cdn.vuetifyjs.com/images/cards/house.jpg",
    show: false,

  }),
  components:{
    Like
  },
  methods:{

  },
  mounted() {
    axios
        .get('./entities.json')
        .then(response => (this.cards = response.data.response))
        .catch(error => console.log(error));
  }

}
</script>

<style scoped>

</style>