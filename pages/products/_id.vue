<template>
  <div>
    <v-container>
      <v-img lazy-src="https://picsum.photos/id/11/10/6" src="https://picsum.photos/id/11/500/300"></v-img>
      <v-card>
        <v-card-title>{{ product.title }}</v-card-title>
        <v-card-text>
          <p>{{ product.description}}</p>
          <p>{{ product.price}} €</p>
          <div class="product-infos">
            <span>TYPE :</span>
            <span class="infos-data">{{ product.type}}</span>
          </div>
          <div class="product-infos">
            <span>AREA :</span>
            <span class="infos-data">{{ product.area}}</span>
          </div>
          <v-btn icon color="pink">
            <v-icon>mdi-heart</v-icon>
          </v-btn>
        </v-card-text>
      </v-card>
    </v-container>
    <!--   <v-row justify="center" align="center">
          <v-col  cols="12" sm="8" md="6">

          </v-col>
    </v-row>-->
  </div>
</template>

<script>
export default {
  async asyncData({ $axios, params, query, error }) {
    let response = await $axios.$get(`products/${params.id}`);
    let product = response.data;
    return { product };
  },
};
</script>

<style>
.product-infos {
  display: flex;
  text-transform: uppercase;
}
.infos-data {
  padding-left: 1em;
}
</style>