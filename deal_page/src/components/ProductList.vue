<template>
  <div class="p-0 m-0">
  <!--Header-->
    <div class="d-flex justify-space-between  px-3">
      <v-icon large>reply</v-icon>
      <div class="mt-3">
         <v-img
        :src="amazonLogo"
        width="80"
        height="auto"
      ></v-img>
      </div>
      <v-icon large>favorite_border</v-icon>
    </div>

<!--Product Image-->
  <v-flex>
    <v-img
      class="text-center mx-auto"
      :src="image"
      width="80%"
      height="auto"
    ></v-img>
  </v-flex>


<!--Percentage Off-->
  <div class="green ">
    <h2 class="text-center white--text">40% OFF</h2>
  </div>


<!--Title and sale price-->
  <v-flex class="d-flex justify-space-between px-3 pt-3">
    <div>
      <h3>Aadi yogi idol</h3>
    </div>
    <div>
      <h3>$451</h3>
    </div>
  </v-flex>


<!--Rating and regular price-->
<v-flex class="d-flex justify-space-between px-3 font-weight-light">
    <div>
      <h6>Aadi yogi idol</h6>
    </div>
    <div>
      <h6>630</h6>
    </div>
  </v-flex>




  </div>
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
