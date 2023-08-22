<template>
  <div class="product-not-found">
    <div class="wrap">
      <p>This Product is unavailable to show</p>
      <button @click="$emit('nextProduct')">Next Product</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "ProductNotFound",
  data() {
    return {
      theme: {
        grey: "#dcdcdc",
        white: "#fff",
        black: "#1e1e1e",
      },
    };
  },
  emits: ["nextProduct"],
};
</script>

<style scoped>
.product-not-found {
  width: 80%;
  height: 80vh;
  background-color: v-bind("theme.white");
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 3rem 5rem;
  border-radius: 5px;
  box-shadow: 0px 0px 5px 2px rgba(0, 0, 0, 0.1);
}
.wrap {
  width: 100%;
  text-align: center;
}

.wrap p {
  margin-bottom: 10px;
  font-size: 20px;
}

.wrap button {
  width: 500px;
  padding: 5px 0;
  border: 4px solid v-bind("theme.black");
  background-color: v-bind("theme.white");
  font-size: 20px;
  font-weight: 600;
  transition: transform 200ms ease-in-out;
  cursor: pointer;
}

.wrap button:active {
  transform: scale(0.9);
}
</style>
