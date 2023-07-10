<template>
  <div class="related_title">
    <ul class="related">
      Related
    </ul>
    <li
      class="related_list"
      v-for="data in datas"
      v-bind:key="data"
      v-bind:title_Props="data"
    >
      {{ data.title }}
    </li>
  </div>
</template>

<script>
import { ref } from "vue";
export default {
  name: "Related_Head",
  setup() {
    const datas = ref([
      {
        title: "worldwide shipping",
      },
      {
        title: "under $50",
      },
      {
        title: "kitten",
      },
      {
        title: "plastic plugs",
      },
      {
        title: "pucker shoes",
      },
      {
        title: "vintage typewriter",
      },
    ]);
    return {
      datas,
    };
  },
};
</script>

<style>
.related_title {
  display: flex;
  padding: 10px 0;
}
.related {
  font-weight: 700;
  padding: 10px 5px 0 10px;
}
.related_list {
  list-style: none;
  padding: 10px 15px;
  border: 1px solid #ededf0;
  color: #4a4b57;
  border-radius: 25px;
  margin: 0 5px;
  background: #ededf0;
}
</style>