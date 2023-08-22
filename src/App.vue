<template>
  <div :class="[category === 'men\'s clothing' ? 'men_colors' : 'women_colors']" class="container">
    <ProductDisplay :category="category" :description="description" :image="image" :price="price" :rating="rating" :title="title" />
  </div>
</template>

<script>
import ProductDisplay from "./components/ProductDisplay.vue";

export default {
  name: "App",
  components: {
    ProductDisplay,
  },
  data() {
    return {
      category: "",
      description: "",
      image: "",
      price: 0,
      rating: {},
      title: "",
      index: 0,
      theme: {
        men_light_blue: "#d6e6ff",
        women_light_pink: "#FDE2FF",
      },
    };
  },
  watch: {
    index: {
      handler: "getProductData",
      immediate: true,
    },
  },
  methods: {
    async getProductData() {
      try {
        if (this.index > 19) {
          this.index = 0;
        }
        const response = await fetch(`https://fakestoreapi.com/products/${this.index + 1}`);
        const product = await response.json();
        this.category = product.category;
        this.description = product.description;
        this.image = product.image;
        this.price = product.price;
        this.rating = { ...product.rating };
        this.title = product.title;
      } catch (error) {
        console.log(error);
      }
    },
    nextProduct() {
      this.index = this.index + 1;
    },
  },
};
</script>

<style scoped>
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  padding-top: 15rem;
}
.men_colors {
  background-color: v-bind("theme.men_light_blue");
  width: 100%;
  height: 70vh;
}
.women_colors {
  background-color: v-bind("theme.women_light_pink");
  width: 100%;
  height: 70vh;
}
</style>
