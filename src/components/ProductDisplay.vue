<template>
  <div class="product-card">
    <div class="image-product">
      <img :src="image" alt="gambar" width="80%" />
    </div>
    <div class="detail-product">
      <h1 class="product-title">{{ title }}</h1>
      <div class="product-category">
        <span>{{ category }}</span>
        <span>{{ rating.rate + "/" + 5 }}</span>
      </div>
      <hr />
      <p class="product-desc">
        {{ description }}
      </p>
      <hr />
      <h2 class="product-price">{{ price }}</h2>
      <div class="button-wrap">
        <button class="button-buy">Buy Now</button>
        <button class="button-next">Next</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ProductDisplay",
  props: {
    category: {
      type: String,
      required: true,
    },
    description: {
      type: String,
      required: true,
    },
    image: {
      type: String,
      required: true,
    },
    price: {
      type: Number,
      required: true,
    },
    rating: {
      type: Object,
      required: true,
    },
    title: {
      type: String,
      required: true,
    },
  },
  data() {
    return {
      theme: {
        men_dark_blue: "#002772",
        men_text: "#3f3f3f",
        women_dark_pink: "#720060",
        black: "#1e1e1e",
        grey: "#dcdcdc",
        white: "#fff",
      },
    };
  },
};
</script>

<style scoped>
.product-card {
  width: 80%;
  background-color: v-bind("theme.white");
  display: flex;
  padding: 3rem 5rem;
  border-radius: 5px;
  box-shadow: 0px 0px 5px 2px rgba(0, 0, 0, 0.1);
}

.image-product {
  width: 40%;
}

.description-product {
  width: 60%;
}
</style>
