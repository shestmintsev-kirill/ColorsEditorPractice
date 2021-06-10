<template>
  <div>
    <div v-for="(item, index) in list.items" :key="item.color" class="item">
      <div class="item-name">
        <input
          @click="confirmChecked(list)"
          v-model="item.checked"
          type="checkbox"
        />
        <span>Item {{ index + 1 }}</span>
      </div>
      <div class="item-description">
        <input
          type="number"
          min="0"
          oninput="validity.valid||(value='');"
          v-model="item.number"
          class="number"
        />
        <input class="item-config" v-model="item.color" type="color" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Item",
  props: {
    list: {
      type: Object,
      default: () => ({}),
    },
  },
  methods: {
    confirmChecked(list) {
      if (list.items.every((i) => i.checked === true)) {
        list.checked = true;
        return false;
      } else if (list.items.every((i) => i.checked === false)) {
        list.checked = false;
        return false;
      }
      return list.items.some((i) => i.checked === true);
    },
  },
};
</script>

<style lang="scss" scoped>
.item-config {
  width: 16px;
  height: 20px;
  border: 0;
  background-color: rgba(250, 250, 250, 0);
}

.section-list {
  &-items {
    width: 100%;

    .item {
      display: flex;
      justify-content: space-around;

      &-description {
        display: flex;
        align-items: baseline;

        .number {
          margin-right: 5px;
          max-width: 30px;
          border: 1px solid rgba(46, 46, 46, 0.1);
        }
      }
    }
  }
}
</style>
