<template>
  <Page style="background-color: azure">
    <ActionBar title="Extra Lessons" />
    <Label text="Welcome to the Extra Curriculum Centre!" class="h2" />
    <!-- <LessonList/> -->
    <TabView androidTabsPosition="bottom">
      <TabViewItem title="Lesson List" class="h2">
        <LessonList @addProduct="addToCart" />
      </TabViewItem>
      <TabViewItem title="Check Out" class="h2">
        <Checkout :cart="cart" @removeProduct="removeFromCart" />
      </TabViewItem>
    </TabView>
  </Page>
</template>

<script>
import LessonList from "./LessonList.vue";
import Checkout from "./Checkout.vue";
export default {
  data() {
    return {
      cart: [],
    };
  },
  components: {
    LessonList,
    Checkout,
  },
  methods: {
    addToCart(product) {
      if (product.spaces > 0) {
        product.spaces -= 1;
        this.cart.push(product);
        alert(product.subject + " added to cart");
      } else {
        alert("No more courses available!");
      }
    },
    removeFromCart(product) {
      if (product.spaces < 20) {
        product.spaces += 1;
        this.cart.splice(this.cart.indexOf(product), 1);
      }
    },
  },
};
</script>

<style scoped></style>
