<template>
  <section class="section-outer">
    <div class="inner">
      <div class="section-list section-border">
        <div class="section-list-items">
          <List :lists="lists" />
        </div>
      </div>
      <div class="section-preview section-border">
        <Preview :lists="lists" />
      </div>
    </div>
  </section>
</template>

<script>
import List from "./List.vue";
import Preview from "./Preview.vue";
export default {
  components: { List, Preview },
  name: "ListsView",
  data: () => ({
    lists: [
      {
        randomColors: false,
        listShow: false,
        checked: true,
        items: [
          {
            checked: false,
            number: 4,
            color: "#fb2d09",
          },
          {
            checked: false,
            number: 4,
            color: "#05ff0d",
          },
          {
            checked: false,
            number: 12,
            color: "#3d08fd",
          },
          {
            checked: false,
            number: 10,
            color: "#ecfb13",
          },
        ],
      },
      {
        randomColors: false,
        listShow: false,
        checked: false,
        items: [
          {
            checked: false,
            number: 4,
            color: "#fb2d09",
          },
          {
            checked: true,
            number: 3,
            color: "#05ff0d",
          },
          {
            checked: false,
            number: 8,
            color: "#3d08fd",
          },
          {
            checked: false,
            number: 10,
            color: "#ecfb13",
          },
        ],
      },
      {
        randomColors: false,
        listShow: false,
        checked: false,
        items: [
          {
            checked: true,
            number: 12,
            color: "#fb2d09",
          },
          {
            checked: true,
            number: 1,
            color: "#05ff0d",
          },
          {
            checked: true,
            number: 8,
            color: "#3d08fd",
          },
          {
            checked: true,
            number: 19,
            color: "#ecfb13",
          },
        ],
      },
      {
        randomColors: false,
        listShow: false,
        checked: false,
        items: [
          {
            checked: false,
            number: 4,
            color: "#fb2d09",
          },
          {
            checked: true,
            number: 77,
            color: "#05ff0d",
          },
          {
            checked: false,
            number: 8,
            color: "#3d08fd",
          },
          {
            checked: false,
            number: 10,
            color: "#ecfb13",
          },
        ],
      },
    ],
  }),
};
</script>

<style scoped lang="scss">
.section-outer {
  padding: 0 20px;
}

.inner {
  display: flex;
  justify-content: space-between;
}

.section-border {
  width: 400px;
  height: auto;
  border: 1px solid black;
  padding: 20px;
}
</style>
