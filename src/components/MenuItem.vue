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
  height: 230px;

  margin: auto;
  width: 60%;
  @media screen and (max-width:480px) {
    width: 100%;
  }
  &__header {
    margin: 0;
    width: 40%;
    list-style: none;
    border: 1px #ccc solid;
    padding: 0;
    .selected {
      padding-right: 5%;
      border-right: 2px #009688 solid;
    }
  }
  li {
    text-align: center;
    cursor: pointer;
    color: #009688;
    font-weight: bold;
    font-size: 20px;

    &:hover {
      background-color: #e0f8f5;
    }
    p {
      margin: 0;
      padding: 20px;
    }
  }
}
</style>