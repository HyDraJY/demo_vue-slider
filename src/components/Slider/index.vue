<script>
let timer = null;
import SliderNav from "./children/Nav";
import SliderList from "./children/List";
export default {
  name: "slider",
  components: {
    SliderNav,
    SliderList
  },
  props: {
    list: {
      type: Array,
      required: true
    }
  },
  data() {
    return {
      current: 0
    };
  },
  computed: {
    total() {
      return this.list ? this.list.length : 0;
    },
    index: {
      get() {
        return this.current;
      },
      set(val) {
        this.current = (val + this.total) % this.total;
      }
    },
    currentPic() {
      return this.list ? this.list[this.index] : null;
    }
  },
  methods: {
    setTimer() {
      this.clearTimer();
      timer = setTimeout(this.timerHandler, 1000);
    },
    clearTimer() {
      clearTimeout(timer);
    },
    timerHandler() {
      this.index += 1;
      this.setTimer();
    }
  },
  mounted() {
    this.setTimer();
  },
  beforeDestroy() {
    this.clearTimer();
  }
};
</script>

<template src='./template.html'></template>
<style src='./style.css'></style>