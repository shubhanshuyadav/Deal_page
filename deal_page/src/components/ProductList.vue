<template>
  <v-container class="p-0 m-0" fill-height >
    <v-content v-for="(product,index) in productList" :key="index">
       <!--Header-->
    <v-flex class="d-flex justify-space-between px-3">
      <v-icon large>reply</v-icon>
      <div class="mt-3">
         <v-img
        :src="amazonLogo"
        width="80"
        height="auto"
      ></v-img>
      </div>
      <v-icon large>favorite_border</v-icon>
    </v-flex>

<!--Product Image-->
  <v-flex>
    <v-img
      class="text-center mx-auto"
      :src="image"
      width="100%"
      height="auto"
    ></v-img>
  </v-flex>


<!--Percentage Off-->
  <v-flex  >
    <div class="d-block green">
      <h2 class="text-center white--text d-block">40% OFF</h2>
    </div>
    <v-flex class="d-flex justify-space-between px-3 pt-3">
      <h3>Aadi yogi idol</h3>
      <h3>$451</h3>
  </v-flex>
  <v-flex class="d-flex justify-space-between px-3 font-weight-light">
    <div>
      <h5 class="font-weight-light">4.5k reviews</h5>
    </div>
    <div>
      <h5 class="font-weight-regular red--line pr-1 text-decoration-line-through">$630</h5>
    </div>
  </v-flex>
  </v-flex>


<!--Title and sale price-->
  


<!--Rating and regular price-->


  <!--Product Description-->
  <v-flex>
    <p class="text--secondary px-2 pt-1">Lorem ipsum dolor sit, vero exercitationem, dolor ratione. Ratione odit nemo voluptate adipisci enim, similique magni natus deserunt veniam esse, nulla repellat aspernatur delectus sed consequatur! Rem libero ullam accusamus ducimus expedita. Ab.</p>
  </v-flex>


 <!--Product Description-->
 <v-flex class="d-flex justify-center pb-3">
   <v-btn class=" white--text" color="#2C2891">Buy Now</v-btn>
 </v-flex>
    </v-content>
  </v-container>
</template>

<script>
import image from "../assets/images/image1.jpeg";
import amazonLogo from "../assets/images/amazon.png";
export default {
  props: ["id"],
  data() {
    return {
      image,
      amazonLogo,
      productList: null,
    };
  },
  created() {
    let url =
      "https://sheets.googleapis.com/v4/spreadsheets/1AxtGuGVOwowUB2T9DDmR80oCJum8lPwtZxhhnwQdxWE/values:batchGet?ranges=A1%3AE100&valueRenderOption=FORMATTED_VALUE&key=AIzaSyBesotaNgSaTUIhrSKjEaExdi-ksKInhoE";

    fetch(url)
      .then((res) => res.json())
      .then((out) => {
        console.log("Checkout this JSON! ", out.valueRanges[0].values);
        this.productList = out.valueRanges[0].values;
      })
      .catch((err) => {
        throw err;
      });
  },
};
</script>

<style>
</style>
