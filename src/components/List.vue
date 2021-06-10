<template>
  <div>
    <div v-for="(list, index) in lists" :key="index" class="list">
      <input
        @click="allChecked(list)"
        v-model="list.checked"
        :type="confirmChecked(list) ? 'radio' : 'checkbox'"
      />
      <span class="showItems" @click.self="showItems(list)"
        >List {{ index + 1 }}</span
      >
      <div v-if="list.listShow">
        <Item :list="list" />
      </div>
    </div>
  </div>
</template>

<script>
import Item from "./Item.vue";
export default {
  name: "list",
  components: { Item },
  props: {
    lists: {
      type: Array,
      default: () => [],
    },
  },
  methods: {
    allChecked(list) {
      if (list.checked) {
        list.items.forEach((i) => {
          i.checked = false;
        });
      } else {
        list.items.forEach((i) => {
          i.checked = true;
        });
      }
    },

    showItems(list) {
      list.listShow = !list.listShow;
    },

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
.section-list {
  .list {
    margin-bottom: 5px;
  }
}

.showItems {
  cursor: pointer;
  padding: 5px;
  border-radius: 5px;
  transition: 0.5s;

  &:hover {
    background: rgba(0, 0, 0, 0.1);
  }
}
</style>
