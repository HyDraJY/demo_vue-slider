<template>
  <!-- <div class="slider__list">
    <transition name="fade" appear mode="out-in">
      <SliderView :src="pic.src" :key="pic.id" />
    </transition>    
  </div>-->
  <transition-group tag="div" class="slider__list" name="fade" appear mode="out-in">
    <SliderView
      v-for="(item, index) in list"
      :src="item.src"
      :key="item.id"
      v-show="index===current"
    ></SliderView>
  </transition-group>
</template>

<script>
import SliderView from "./View";
export default {
  name: "slider-list",
  props: ["pic", "list", "current"],
  components: {
    SliderView
  }
};
</script>

<style>
.slider__list {
  position: absolute;
  width: 100%;
  height: 100%;
  top: 0;
  left: 0;
}

.fade-enter,
.fade-leave-to {
  opacity: 0;
}
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s;
}
.fade-enter-to,
.fade-leave {
  opacity: 1;
}
</style>