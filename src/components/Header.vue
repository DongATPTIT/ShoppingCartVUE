<template>
  <div class="header-sort">
    <div class="ul-list">
      <li>
        <button class="options">
          Useless first
          <img :src="imageSrc" alt="" />
        </button>
      </li>
      <li>
        <button class="options">
          Condition
          <img :src="imageSrc" alt="" />
        </button>
      </li>
      <li>
        <button class="options">
          Delivery options
          <img :src="imageSrc" alt="" />
        </button>
      </li>
      <select name="" class="sort">
        <option
          v-for="sort in sorts"
          v-bind:key="sort.id"
          :value="sort.id"
          v-bind:PropsOption="sort"
        >
          {{ sort.title }}
        </option>
      </select>
    </div>

    <div class="action">
      <div class="action-tt">
        <li><a href="">Show all</a></li>
        <li><a href="">Auction</a></li>
        <li><a href="">Buy now</a></li>
      </div>

      <div class="item">
        <img :src="imgView" alt="" @click="selectItem('2')" />
        <img
          class="item-active"
          @click="selectItem('4')"
          :src="imgActive"
          alt=""
        />
      </div>
    </div>
  </div>
  <Related_Head />
</template>

<script>
import Related_Head from "./Related.vue";
import EventBus from "./EventBus";
import { ref } from "vue";
export default {
  name: "HeaderApp",
  components: {
    Related_Head,
  },
  setup() {
    const sorts = ref([
      {
        title: "Low",
      },
      {
        title: "Key",
      },
    ]);
    return {
      sorts,
    };
  },
  data() {
    return {
      imageSrc: require("@/assets/HeaderApp/RightIcons.png"),
      imgActive: require("@/assets/HeaderApp/Vector.png"),
      imgView: require("@/assets/HeaderApp/viewlist.png"),
    };
  },
  methods: {
    selectItem(item) {
      EventBus.$emit("update-body-component", item);
    },
  },
};
</script>

<style>
.header-sort {
  display: flex;
  padding: 30px 5px;
  justify-content: space-between;
  flex-direction: row;
  align-items: center;
}
.ul-list {
  text-decoration: none;
  list-style: none;
  display: flex;
}

.ul-list .options {
  text-decoration: none;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 5px;
  margin: 5px;
  background: #fff;
  color: #787885;
  display: flex;
  align-items: center;
}
.options :hover {
  cursor: pointer;
}
.action {
  align-items: center;
  display: flex;
}
.action-tt {
  display: flex;
  list-style: none;
}
.action-tt > li > a {
  text-decoration: none;
  padding: 10px;
  border-radius: 5px;
  margin: 5px;
  color: #787885;
  display: flex;
  align-items: center;
  background: #ebf2ff;
}
.item {
  color: #000;
  padding: 0 5px 0 15px;
}
.item-active {
  padding: 0 5px;
}
.sort {
  margin: 7px 10px;
  padding: 0px 20px;
  border-radius: 5px;
  border: #787885;
}
</style>