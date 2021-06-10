<template>
  <div>
    <div
      v-for="(list, index) in lists"
      :key="index"
      class="section-preview-items"
    >
      <div class="section-preview-items-name">
        <span>List {{ index + 1 }}</span>
        <button
          class="section-preview-items-name-btn"
          :class="{ btnDisabled: !list.listShow }"
          @click="
            list.listShow
              ? (list.randomColors = !list.randomColors)
              : list.randomColors
          "
        >
          Перемешать
        </button>
      </div>
      <div v-if="list.listShow">
        <div :class="{ wrapper: list.randomColors }">
          <div
            v-for="item in list.items"
            :key="item.color"
            :class="{ wrapper: list.randomColors }"
          >
            <div class="section-preview-items-colors" v-if="item.checked">
              <div
                @click.self="removeItem(item)"
                v-for="(color, index) in Number(item.number)"
                :key="index"
                :style="{ background: item.color }"
                class="item-color"
              ></div>
            </div>
          </div>
        </div>
        <!-- Реализация перемешивания -->

        <!-- <div class="random-wrapper">
              <div
                @click.self="removeItem(item)"
                v-for="item in Number(randomItems(list.items))"
                :key="item"
                class="item-color"
              ></div>
            </div> -->

        <!-- Реализация перемешивания -->
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Preview",
  props: {
    lists: {
      type: Array,
      default: () => [],
    },
  },
  methods: {
    //* Реализация перемешивания

    // randomItems(item) {
    //   item.randomColors = !item.randomColors;
    //   const numberArr = [];
    //   item.forEach((i) => {
    //     numberArr.push(i.number);
    //   });
    //   const result = numberArr.reduce((acc, value) => acc + value);
    //   return Number(result);
    // },

    //* Реализация перемешивания

    removeItem(item) {
      item.number--;
    },
  },
};
</script>

<style lang="scss" scoped>
.section-preview {
  &-items {
    border: 1px solid black;
    padding: 5px;
    margin-bottom: 5px;

    &-name {
      display: flex;
      justify-content: space-between;
      align-items: baseline;
      margin-bottom: 5px;

      &-btn {
        background: rgb(153, 200, 255);
        border: 0;
        padding: 5px;
        border-radius: 5px;
        box-shadow: 1px 1px 15px -1px rgba(34, 60, 80, 0.22);
        cursor: pointer;
        transition: 0.3s;

        &:hover {
          box-shadow: 1px 1px 15px -1px rgba(34, 60, 80, 0.6);
        }
      }
    }

    &-colors {
      display: flex;
      flex-wrap: wrap;
      margin-top: 4px;
    }
  }
}

.item-color {
  background: rgb(255, 114, 114);
  width: 10px;
  height: 10px;
  margin: 1px 1px;
}

.wrapper {
  display: flex;
  flex-wrap: wrap;
  margin: 0;
}

.btnDisabled {
  background: rgb(180, 180, 180);

  &:hover {
    box-shadow: none;
  }
}
</style>
