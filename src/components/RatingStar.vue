<template>
  <div class="wrap">
    <div>
      <div v-if="category === 'men\'s clothing'" class="circle" :class="[rating.rate > 0.5 ? 'fill-circle-men' : 'circle-men']"></div>
      <div v-else class="circle" :class="[rating.rate > 0.5 ? 'fill-circle-women' : 'circle-women']"></div>
    </div>
    <div>
      <div v-if="category === 'men\'s clothing'" class="circle" :class="[rating.rate > 1.5 ? 'fill-circle-men' : 'circle-men']"></div>
      <div v-else class="circle" :class="[rating.rate > 1.5 ? 'fill-circle-women' : 'circle-women']"></div>
    </div>
    <div>
      <div v-if="category === 'men\'s clothing'" class="circle" :class="[rating.rate > 2.5 ? 'fill-circle-men' : 'circle-men']"></div>
      <div v-else class="circle" :class="[rating.rate > 2.5 ? 'fill-circle-women' : 'circle-women']"></div>
    </div>
    <div>
      <div v-if="category === 'men\'s clothing'" class="circle" :class="[rating.rate > 3.5 ? 'fill-circle-men' : 'circle-men']"></div>
      <div v-else class="circle" :class="[rating.rate > 3.5 ? 'fill-circle-women' : 'circle-women']"></div>
    </div>
    <div>
      <div v-if="category === 'men\'s clothing'" class="circle" :class="[rating.rate > 4.5 ? 'fill-circle-men' : 'circle-men']"></div>
      <div v-else class="circle" :class="[rating.rate > 4.5 ? 'fill-circle-women' : 'circle-women']"></div>
    </div>
  </div>
</template>

<script>
export default {
  name: "RatingStar",
  props: {
    rating: {
      type: Object,
      required: true,
    },
    category: {
      type: String,
      required: true,
    },
  },
  data() {
    return {
      theme: {
        men_dark_blue: "#002772",
        women_dark_pink: "#720060",
      },
    };
  },
};
</script>

<style scoped>
.wrap {
  display: flex;
  justify-content: space-around;
  align-items: center;
}

.circle {
  width: 18px;
  height: 18px;
  border-radius: 50%;
  margin-right: 2px;
}

.circle-men {
  border: 2px solid v-bind("theme.men_dark_blue");
}

.circle-women {
  border: 2px solid v-bind("theme.women_dark_pink");
}

.fill-circle-men {
  background-color: v-bind("theme.men_dark_blue");
}

.fill-circle-women {
  background-color: v-bind("theme.women_dark_pink");
}
</style>
