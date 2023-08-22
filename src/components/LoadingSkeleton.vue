<template>
  <div class="product-skeleton">
    <div class="image-product"></div>
    <div class="detail-product">
      <h1></h1>
      <div class="product-info">
        <div class="category"></div>
        <div class="product-rating"></div>
      </div>
      <br />
      <p class="product-desc"></p>
      <br />
      <h2 class="product-price"></h2>
    </div>
  </div>
</template>

<script>
export default {
  name: "LoadingSkeletonr",
  data() {
    return {
      theme: {
        white: "#fff",
      },
    };
  },
};
</script>

<style scoped>
.product-skeleton {
  width: 80%;
  height: 80vh;
  background-color: v-bind("theme.white");
  display: flex;
  padding: 3rem 5rem;
  border-radius: 5px;
  box-shadow: 0px 0px 5px 2px rgba(0, 0, 0, 0.1);
}

.image-product {
  width: 30%;
  height: 100%;
  margin-right: 10%;
  animation: pulse 2s infinite ease-in-out;
}

.detail-product {
  width: 60%;
}

.detail-product h1 {
  margin-bottom: 16px;
  height: 80px;
  animation: pulse 2s infinite ease-in-out;
}

.product-info {
  display: flex;
  justify-content: space-between;
  margin-bottom: 12px;
}
.category {
  height: 20px;
  width: 80px;
  animation: pulse 2s infinite ease-in-out;
}

.product-rating {
  height: 20px;
  width: 100px;
  animation: pulse 2s infinite ease-in-out;
}

.product-desc {
  margin-top: 2 rem;
  height: 50%;
  width: 100%;
  animation: pulse 2s infinite ease-in-out;
}

.product-price {
  margin: 12px 0;
  width: 80px;
  height: 30px;
  animation: pulse 2s infinite ease-in-out;
}

@keyframes pulse {
  0% {
    background-color: #94a3b8;
  }

  50% {
    background-color: #cbd5e1;
  }

  100% {
    background-color: #94a3b8;
  }
}
</style>
