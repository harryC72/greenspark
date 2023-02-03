<script lang="ts">
import LogoGreenpark from "./icons/LogoGreenpark.vue";
import Tooltip from "./Tooltip.vue";
import Colors from "./Colors.vue";
export default {
  components: {
    LogoGreenpark,
    Tooltip,
    Colors,
  },
  props: [
    "action",
    "active",
    "amount",
    "id",
    "linked",
    "selectedColor",
    "type",
    "changeLinkedState",
    "changeActiveState",
    "changeSelectedColor",
  ],

  computed: {
    style() {
      return `background-color: var(--${this.selectedColor})`;
    },
  },
  mounted() {
    console.log(
      "FROM Product",
      this.action,
      this.active,
      this.amount,
      this.id,
      this.linked,
      this.selectedColor,
      this.type
    );
  },
};
</script>
<template>
  <div class="top-box" :style="style">
    <div><LogoGreenpark /></div>
    <div class="top-text-box">
      <div>This product {{ action }}</div>
      <div>{{ amount }} {{ type }}</div>
    </div>
  </div>
  <div class="text">
    <div>
      <div>
        Link to Public Profile<span
          ><Tooltip
            class="tooltip"
            text="This widget links directly to your public profile so that you can easily share your impact with your customers. Turn it off here if you do not want the badge to link to it."
            actionCall="View Public	Profile"
        /></span>
      </div>
      <input
        type="checkbox"
        name="linked"
        :id="id"
        :checked="linked"
        @change="changeLinkedState(id)"
      />
    </div>
    <div>
      <div>Badge colour</div>
      <Colors
        :selectedColor="selectedColor"
        :changeSelectedColor="changeSelectedColor"
        :id="id"
      />
    </div>
    <div>
      <div>Activate badge</div>
      <label class="switch">
        <input
          type="checkbox"
          name="active"
          :checked="active"
          :id="id"
          @change="changeActiveState(id)"
        />
        <span class="slider round"></span>
      </label>
    </div>
  </div>
</template>
<style scoped>
input[type="checkbox"] {
  accent-color: var(--green);
}
.top-box {
  margin-top: 20px;
  width: 221px;
  padding: 10px 16px;
  border-radius: 6px;
  display: flex;
  color: var(--white);
}
.top-text-box {
  padding-left: 12px;
}
.text {
  width: 221px;
  color: var(--green);
  margin-bottom: 160px;
}

.text div {
  display: flex;
  justify-content: space-between;
}

.switch {
  position: relative;
  display: inline-block;
  width: 46px;
  height: 23px;
}

.switch input {
  opacity: 0;
  width: 0;
  height: 0;
}

.slider {
  position: absolute;
  cursor: pointer;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: var(--white);

  background: #f9f9f9;
  border: 0.58978px solid #f2ebdb;
  box-shadow: 0px 0px 1.17956px rgba(0, 0, 0, 0.35);
  border-radius: 29.489px;

  -webkit-transition: 0.4s;
  transition: 0.4s;
}

.slider:before {
  position: absolute;
  content: "";
  height: 23px;
  width: 23px;
  top: -0.8px;
  background: #f9f9f9;
  border: 0.58978px solid #f2ebdb;
  box-shadow: 0px 0px 1px rgba(0, 0, 0, 0.35);
  border-radius: 29px;
  -webkit-transition: 0.4s;
  transition: 0.4s;
}

input:checked + .slider {
  background-color: var(--green);
  left: 1px;
}

input:focus + .slider {
  box-shadow: 0 0 1px var(--white);
}

input:hover + .slider:before {
  outline: 7px solid #afc6bd;
  background: #f9f9f9;
}

input:checked + .slider:before {
  -webkit-transform: translateX(20px);
  -ms-transform: translateX(20px);
  transform: translateX(20px);
}

@media only screen and (max-width: 600px) {
  .text {
    margin-bottom: 38px;
  }
}
</style>