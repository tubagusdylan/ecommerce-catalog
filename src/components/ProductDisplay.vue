<template>
  <div class="product-card">
    <div class="image-product">
      <img :src="image" alt="gambar" width="80%" />
    </div>
    <div class="detail-product">
      <h1 class="product-title" :class="[category === 'men\'s clothing' ? 'men-colors' : 'women-colors']">{{ title }}</h1>
      <div class="product-info">
        <div>
          <span>{{ category }}</span>
        </div>
        <div class="product-rating">
          <span>{{ rating.rate + "/" + 5 }}</span>
          <RatingStar :rating="rating" :category="category" />
        </div>
      </div>
      <hr />
      <p class="product-desc">
        {{ description }}
      </p>
      <hr />
      <h2 class="product-price" :class="[category === 'men\'s clothing' ? 'men-colors' : 'women-colors']">{{ "$" + price }}</h2>
      <div class="button-wrap">
        <button class="button-buy" :class="[category === 'men\'s clothing' ? 'men-bg-colors' : 'women-bg-colors']">Buy Now</button>
        <button class="button-next" :class="[category === 'men\'s clothing' ? 'men-btn-colors' : 'women-btn-colors']">Next Product</button>
      </div>
    </div>
  </div>
</template>

<script>
import RatingStar from "./RatingStar.vue";

export default {
  name: "ProductDisplay",
  components: {
    RatingStar,
  },
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

.detail-product {
  width: 60%;
}

.product-title {
  margin-bottom: 16px;
}

.product-info {
  display: flex;
  justify-content: space-between;
  margin-bottom: 12px;
}

.product-rating {
  display: flex;
  gap: 10px;
}

.product-desc {
  margin-top: 2rem;
  height: 50%;
  font-size: 20px;
}

.product-price {
  margin: 12px 0;
}

.button-wrap {
  width: 100%;
  text-align: center;
}

button {
  width: 49%;
  padding: 10px 0;
  border: none;
  font-size: 20px;
  font-weight: 600;
  cursor: pointer;
}
.button-buy {
  margin-right: 2%;
  color: v-bind("theme.white");
  border-radius: 7px;
  transition: transform 200ms ease-in-out;
}

.button-buy:active {
  transform: scale(0.9);
}

.button-next {
  background-color: v-bind("theme.white");
  border-radius: 7px;
  transition: transform 200ms ease-in-out;
}

.button-next:active {
  transform: scale(0.9);
}

.men-colors {
  color: v-bind("theme.men_dark_blue");
}
.women-colors {
  color: v-bind("theme.women_dark_pink");
}

.men-btn-colors {
  color: v-bind("theme.men_dark_blue");
  border: 4px solid v-bind("theme.men_dark_blue");
}
.women-btn-colors {
  color: v-bind("theme.men_dark_blue");
  border: 4px solid v-bind("theme.women_dark_pink");
}

.men-bg-colors {
  background-color: v-bind("theme.men_dark_blue");
  border: 4px solid v-bind("theme.men_dark_blue");
}
.women-bg-colors {
  background-color: v-bind("theme.women_dark_pink");
  border: 4px solid v-bind("theme.women_dark_pink");
}
</style>
