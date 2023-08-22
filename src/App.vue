<template>
  <div>
    <div v-if="category === null" class="container skeleton-color">
      <LoadingSkeleton />
    </div>
    <div v-else-if="category === ''" class="container unavailable-color">
      <ProductNotFound @nextProduct="nextProduct" />
    </div>
    <div v-else :class="[category === 'men\'s clothing' ? 'men_colors' : 'women_colors']" class="container">
      <ProductDisplay :category="category" :description="description" :image="image" :price="price" :rating="rating" :title="title" @nextProduct="nextProduct" />
    </div>
  </div>
</template>

<script>
import ProductDisplay from "./components/ProductDisplay.vue";
import ProductNotFound from "./components/ProductNotFound.vue";
import LoadingSkeleton from "./components/LoadingSkeleton.vue";

export default {
  name: "App",
  components: {
    ProductDisplay,
    ProductNotFound,
    LoadingSkeleton,
  },
  data() {
    return {
      category: null,
      description: "",
      image: "",
      price: 0,
      rating: {},
      title: "",
      index: 0,
      theme: {
        men_light_blue: "#d6e6ff",
        women_light_pink: "#FDE2FF",
        grey: "#dcdcdc",
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
        if (product.category === "electronics" || product.category === "jewelery") {
          this.category = "";
          return;
        }
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
      this.category = null;
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

.unavailable-color {
  background-color: v-bind("theme.grey");
  width: 100%;
  height: 70vh;
}

.skeleton-color {
  background-color: #94a3b8;
  width: 100%;
  height: 70vh;
}
</style>
