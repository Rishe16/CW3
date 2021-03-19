<template>
  <StackLayout>
    <Label class="h2 text-center" text="Shopping Cart" />
    <Label class="h2 text-center" text="(Tap a product to remove it)" />
    <ListView for="product in cart" @itemTap="onItemTap">
      <v-template>
        <StackLayout>
          <Label :text="product.subject" />
          <Label :text="`price: ${product.price}`" />
        </StackLayout>
      </v-template>
    </ListView>
    <TextField hint="Name" v-model="name" />
    <TextField hint="Phone Number" v-model="phonenumber" />
    <Button @tap="submitOrder" text="Submit Order" />
  </StackLayout>
</template>

<script>
export default {
  props: ["cart"],
  data() {
    return {
      name: "",
      phonenumber: "",
    };
  },
  methods: {
    onItemTap(event) {
      this.$emit("removeProduct", event.item);
    },
    submitOrder() {
      if (this.name == "" || this.phonenumber == "") {
        alert("Please fill in both fields");
        return;
      } else {
        alert("An order is placed by " + this.name + " at " + this.phonenumber);
      }
    },
  },
};
</script>
