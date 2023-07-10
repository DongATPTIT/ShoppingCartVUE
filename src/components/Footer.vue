<template>
  <div class="FooterApp">
    <div class="row-all">
      <ul
        class="row-list"
        v-for="footerData in footerDatas"
        v-bind:key="footerData"
        v-bind:PropsFooter="footerData"
      >
        <li class="col-list">
          <img class="footer_img" :src="footerData.srcImg" alt="" />
          <h1 class="footer_title">{{ footerData.title }}</h1>
          <p class="footer_des">{{ footerData.des }}</p>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import { ref } from "vue";
export default {
  name: "FooterApp",
  setup() {
    const footerDatas = ref([
      {
        srcImg: require("@/assets/FooterApp/idea.png"),
        title: "Clear & Usable user flows",
        des: "Let’s boost yout marketplace",
      },
      {
        srcImg: require("@/assets/FooterApp/Vector.png"),
        title: "Fine & Styled components",
        des: "Speed up with Setproduct templates",
      },
      {
        srcImg: require("@/assets/FooterApp/mau.png"),
        title: "Customizable & Reusable",
        des: "Take our UX patterns and rebuild",
      },
    ]);
    return {
      footerDatas,
    };
  },
};
</script>

<style>
.FooterApp {
  padding: 0px 10px;
  margin-bottom: 50px;
}
.row-all {
  list-style: none;
  display: flex;
  flex-wrap: wrap;
}
.row-list {
  width: 31.333333%;
  list-style: none;
  background: #ededf0;
  padding: 30px 0;
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  margin: 10px;
  border-radius: 5px;
}
.footer_img {
  align-items: center;
}
.footer_title {
  font-size: 20px;
}
.footer_des {
  font-size: 14px;
}
</style>