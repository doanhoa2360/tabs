<template>
  <div class="tabs">
    <ul class="tabs__header">
      <li
        v-for="title in tabTitles"
        :key="title"
        :class="{ selected: title == selectTitle }"
        @click="selectTitle = title"
      >
        <p>{{ title }}</p>
      </li>
    </ul>

    <slot />
  </div>
</template>
<script>
import { provide, ref } from "vue";
export default {
  setup(props, { slots }) {
    const itemIcon = ref(slots.default().map((table) => table.props.class));

    const tabTitles = ref(slots.default().map((tab) => tab.props.title));
    console.log(itemIcon);
    const selectTitle = ref(tabTitles.value[0]);
    provide("selectTitle", selectTitle);
    return {
      itemIcon,
      selectTitle,
      tabTitles,
    };
  },
};
</script>
<style lang="scss">
.tabs {
  display: flex;
  height: 200px;
  margin: auto;
  width: 60%;
  &__header {
    width: 40%;
    list-style: none;
.selected {
      
          width: 50%;
          padding-right: 5%;
          border-right: 2px rgb(69, 31, 239) solid;
        
      }
    li {
      display: flex;
      cursor: pointer;
      color: rgb(43, 43, 233);
      font-weight: bold;
      
      &:hover {
        color: rgb(43, 43, 233, 0.7);
      }
      
    }
  }
}
::-webkit-scrollbar {
  width: 20px;
}

/* Track */
::-webkit-scrollbar-track {
  box-shadow: inset 0 0 5px transparent;
  border-radius: 10px;
}

/* Handle */
::-webkit-scrollbar-thumb {
  background: transparent;
  border-radius: 10px;
}

/* Handle on hover */
::-webkit-scrollbar-thumb:hover {
  background: transparent;
}

</style>