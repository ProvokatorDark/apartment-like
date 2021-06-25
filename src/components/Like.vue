<template>
  <v-btn
      v-bind:class="{ active: isActive }"
      v-on:click="toggleLike"
      icon>
    <v-icon>mdi-heart</v-icon>
  </v-btn>
</template>

<script>
export default {
  name: "Like",
  data: () => ({
    isActive:false
  }),
  methods:{
    toggleLike:function (){
      this.isActive=!this.isActive;
    }
  },
}

</script>

<style>
.theme--light.v-btn.v-btn--icon.active{
    color: palevioletred;
  }
</style>