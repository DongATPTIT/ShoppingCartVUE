<template>
  <div class="bodyApp">
    <component :is="currentComponent"></component>
    <select name="" id="" v-model="sortBy">
      <option value="low">Low</option>
      <option value="high">Key</option>
    </select>
    <div
      class="bodyApp-list"
      v-for="dataBody in sortedDataBodys"
      v-bind:key="dataBody.title"
      v-bind:BodyList-Prop="dataBody"
    >
      <div class="item-list">
        <img class="item_img" :src="dataBody.src_img" alt="" />
        <p class="item_title">{{ dataBody.title }}</p>
        <h1 class="item_price">{{ dataBody.price }}</h1>
        <p class="item_des">{{ dataBody.des }}</p>
      </div>
    </div>
  </div>
</template>

<script>
import { ref, computed, watch } from "vue";
import EventBus from "./EventBus";
import BodyColVue from "./BodyCol.vue";
import BodyRowVue from "./BodyRow.vue";
export default {
  name: "BodyApp",
  components: {
    BodyColVue,
    BodyRowVue,
  },
  data() {
    const sortBy = ref("");
    const dataBodys = ref([
      {
        src_img: require("@/assets/BodyApp/maydanhchu.png"),
        title:
          "Vintage Typewriter to post awesome stories about UI design and webdev.",
        price: "$49.50",
        des: "Eligible for Shipping To Mars or somewhere else",
      },
      {
        src_img: require("@/assets/BodyApp/giay.png"),
        title:
          "Lee Pucker design. Leather botinki for handsome designers. Free shipping.",
        price: "$13.95",
        des: "1258 bids, 359 watchers $5.95 for shipping",
      },
      {
        src_img: require("@/assets/BodyApp/cat.png"),
        title:
          "Timesaving kitten to save months on development. Playful, cute, cheap!",
        price: "$128.99",
        des: "Eligible for nothing :(",
      },
      {
        src_img: require("@/assets/BodyApp/4.png"),
        title:
          "Plastic useless plugs and tubes for high-fidelity prototyping. Fit & Eat!",
        price: "$12.48",
        des: "Wordwide shitting available Buyers protection possible!",
      },
      {
        src_img: require("@/assets/BodyApp/5.png"),
        title:
          "Creativity stimulating lotion. Drink every morning to generate better ideas!",
        price: "$12.48",
        des: "Wordwide shifting available Buyers protection possible!",
      },
      {
        src_img: require("@/assets/BodyApp/6.png"),
        title: "Prototyping items to create a lot if useless things...",
        price: "$128.99",
        des: "Showcasing onHovered state",
      },
      {
        src_img: require("@/assets/BodyApp/7.png"),
        title: "John Von Ebalkin SPRING ",
        price: "$13.95",
        des: "1258 bids, 359 watchers $5.95 for shipping",
      },
      {
        src_img: require("@/assets/BodyApp/8.png"),
        title:
          "Envelope, Stripes, Pencil and etc. Purchase this kit today and feel OKAY",
        price: "$9.50",
        des: "Eligible for Shipping To Mars or somewhere else",
      },
      {
        src_img: require("@/assets/BodyApp/9.png"),
        title: "Professional teadrinking set for every designer and developer",
        price: "$128.99",
        des: "Eligible for nothing :(",
      },
      {
        src_img: require("@/assets/BodyApp/10.png"),
        title: "One string Bonsai description",
        price: "$11.68",
        des: "Wordwide shifting available Buyers protection possible!",
      },
      {
        src_img: require("@/assets/BodyApp/11.png"),
        title:
          "Simply best item in town to shine bright with your Nine Inch Nails",
        price: "$1.25",
        des: "Eligible for Shipping To Mars or somewhere else",
      },
      {
        src_img: require("@/assets/BodyApp/12.png"),
        title:
          "KISTOCHKI & KRASIBO. Top cosmetics brand from Chelyabinsk is here!",
        price: "$23.25",
        des: "1258 bids, 359 watchers $5.95 for shipping",
      },
    ]);
    const sortedDataBodys = computed(() => {
      if (sortBy.value === "low") {
        return dataBodys.value.slice().sort((a, b) => {
          return (
            parseFloat(a.price.substring(1)) - parseFloat(b.price.substring(1))
          );
        }); // Sắp xếp theo giá tăng dần
      } else if (sortBy.value === "high") {
        return dataBodys.value.slice().sort((a, b) => {
          return (
            parseFloat(b.price.substring(1)) - parseFloat(a.price.substring(1))
          );
        }); // Sắp xếp theo giá giảm dần
      }
      return dataBodys.value; // Trả về danh sách không được sắp xếp
    });

    watch(
      () => sortBy.value,
      () => {
        console.log(sortedDataBodys.value); // Hiển thị giá trị sortedDataBodys trong console
      }
    );
    return {
      currentComponent: "Component2",
      sortBy,
      dataBodys,
      sortedDataBodys,
    };
  },
  mounted() {
    EventBus.on("update-body-component", this.updateComponent);
  },
  beforeUnmount() {
    EventBus.off("update-body-component", this.updateComponent);
  },
  methods: {
    updateComponent(item) {
      if (item === "2") {
        this.currentComponent = "Component2";
      } else if (item === "4") {
        this.currentComponent = "Component4";
      }
    },
  },
};
</script>

<style>
.bodyApp {
  padding: 0px 35px;
  display: flex;
  flex-wrap: wrap;
}
.bodyApp-list {
  width: 22%;
  margin: 10px 15px;
}
.item_title {
  font-size: 16px;
  line-height: 24px;
}
.item_price {
  font-weight: 700;
  font-size: 24px;
  padding: 10px 0;
}
.item_des {
  font-size: 14px;
  line-height: 20px;
}
.item_price,
.item_des,
.item_title
/* .item_img { */ {
  padding: 10px 20px;
}
</style>