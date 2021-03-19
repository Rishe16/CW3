<template>
  <StackLayout>
    <Label
      class="h2 p-10"
      textWrap="true"
      text="Tap a product to add it to cart"
    />
    <ListView for='product in products' @itemTap="onItemTap">
      <v-template>
        <StackLayout>
          <Label :text="product.subject" />
          <Label :text="`location: ${product.location}`" />
          <Label :text="`price: ${product.price}`" />
          <Label :text="`spaces: ${product.spaces}`" />
        </StackLayout>
      </v-template>
    </ListView>
  </StackLayout>
</template>

<script>
export default {
  data() {
    return {
      products: [
        { subject: "Maths Classes", location: "Hendon", price: 40, spaces: 20 },
        { subject: "Football", location: "Collindale", price: 6, spaces: 20 },
        { subject: "Homework Club", location: "Egdware", price: 25, spaces: 20 },
        { subject: "Survival Skills", location: "Kings Cross", price: 15, spaces: 20 },
        { subject: "Drama and Music", location: "Tooting", price: 3, spaces: 20 },
      ],
    };
  },
  methods: {
    onItemTap(event) {
      this.$emit('addProduct', event.item);
      //alert(event.item.subject + 'has been added to the cart.')
          //console.log('item tapped');
    },
  },
};
</script>
