<script lang="ts">
import { defineComponent } from "vue";
export default defineComponent({
  props: {
    selectedColor: String,
    changeSelectedColor: Function,
    id: Number,
  },

  mounted() {
    console.log(
      "FROM COLORS",
      this.selectedColor,
      this.changeSelectedColor,
      this.id
    );
  },
});
</script>
<template>
  <div class="color-container">
    <div
      class="color-box blue"
      :class="selectedColor === 'blue' && 'selected'"
      @click="changeSelectedColor?.(id, 'blue')"
    ></div>
    <div
      class="color-box green"
      :class="selectedColor === 'green' && 'selected'"
      @click="changeSelectedColor?.(id, 'green')"
    ></div>
    <div
      class="color-box beige"
      :class="selectedColor === 'beige' && 'selected'"
      @click="changeSelectedColor?.(id, 'beige')"
    ></div>
    <div
      class="color-box white"
      :class="selectedColor === 'white' && 'selected'"
      @click="changeSelectedColor?.(id, 'white')"
    ></div>
    <div
      class="color-box black"
      :class="selectedColor === 'black' && 'selected'"
      @click="changeSelectedColor?.(id, 'black')"
    ></div>
  </div>
</template>
<style scoped>
.container {
  display: flex;
}
.color-box {
  width: 16px;
  height: 16px;
}

.color-box:hover {
  opacity: 0.8;
}
.blue {
  background-color: var(--blue);
}
.green {
  background-color: var(--green);
}
.beige {
  background-color: var(--beige);
}
.white {
  background-color: var(--white-box);
}

.black {
  background-color: var(--black);
}

.selected {
  box-sizing: border-box;
  width: 16px;
  height: 16px;
  left: 0px;
  top: 0px;
  border: 1.5px solid var(--border);
  box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.01);
}
</style>
