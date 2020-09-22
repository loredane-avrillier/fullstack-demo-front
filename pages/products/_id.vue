<template>
  <div>
    <v-row>
      <v-col cols="12">
        <v-btn class="ma-2" text nuxt to="/">
          <v-icon dark left>mdi-arrow-left</v-icon> Retour
        </v-btn>
      </v-col>
    </v-row>
    <v-row>
      <v-col cols="12" md="6">
        <v-img
          lazy-src="https://picsum.photos/id/11/10/6"
          src="https://picsum.photos/id/11/500/300"
        ></v-img>
      </v-col>
      <v-col cols="12" md="6">
        <v-container>
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
      </v-col>
    </v-row>

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

<style lang="scss">
.product-infos {
  display: flex;
  text-transform: uppercase;
  .infos-data {
    padding-left: 1em;
  }
}
</style>