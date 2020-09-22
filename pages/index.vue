<template>
  <v-row justify="center" align="center">
    <!--  <v-col cols="12">
        <v-parallax src="https://cdn.vuetifyjs.com/images/parallax/material.jpg"></v-parallax>
    </v-col>-->
    <v-col cols="12" sm="8" md="6" v-for="product in products" :key="product.id">
      <!--    <div class="text-center">
         <logo />
        <vuetify-logo /> 
      </div>-->

      <v-card>
        <v-card-title class="headline">{{ product.title }}</v-card-title>
        <v-card-text>
          <v-img
            lazy-src="https://picsum.photos/id/11/10/6"
            src="https://picsum.photos/id/11/500/300"
          >></v-img>
          <div class="product-infos">
            <div>
              <p>{{ product.type }}</p>
              <p>{{ product.area }}</p>
            </div>
            <span class="price">{{ product.price }} €</span>
          </div>
        </v-card-text>
        <v-card-actions>
          <v-spacer />
          <v-btn icon color="pink">
            <v-icon>mdi-heart</v-icon>
          </v-btn>
          <v-btn depressed nuxt :to="'/products/' + product.id">Voir</v-btn>
        </v-card-actions>
      </v-card>
    </v-col>
  </v-row>
</template>

<script>
import Logo from "~/components/Logo.vue";
import VuetifyLogo from "~/components/VuetifyLogo.vue";

export default {
  components: {
    Logo,
    VuetifyLogo,
  },
  async asyncData({ $axios, params, query, error }) {
    let response = await $axios.$get("/products");
    let products = response.data;
    return { products };
  },
};
</script>
<style>
.product-infos {
  display: flex;
  justify-content: space-between;
  padding-top: 1em;
}
.price {
  font-weight: bold;
  font-size: 1.5em;
}
</style>