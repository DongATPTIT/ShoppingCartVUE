<template>
  <div class="item-list">
    <img class="item_img" :src="dataBody.src_img" alt="" />
    <p class="item_title">{{ dataBody.title }}</p>
    <h1 class="item_price">{{ dataBody.price }}</h1>
    <p class="item_des">{{ dataBody.des }}</p>
  </div>
</template>

<script>
export default {
  name: "BodyRow",
};
</script>

<style>
</style>