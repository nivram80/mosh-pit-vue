<template>
  <div
    class="dropdown"
    v-click-outside="hideOptions"
  >
    <div
      class="select"
      @click="toggleOptions"
    >
      <div class="placeholder">{{placeholder}}</div>
      <KeyboardArrowDownIcon />
    </div>
    <div
      class="options"
      v-show="showOptions"
    >
      <div
        class="option"
        v-for="option in options"
        :key="option"
      >
        {{option}}
      </div>
    </div>
  </div>
</template>

<script>
import KeyboardArrowDownIcon from '@/components/icons/KeyboardArrowDownIcon.vue'
import { ClickOutsideDirective } from '@/directives/ClickOutsideDirective.js';

export default {
  name: "Dropdown",
  components: {
    KeyboardArrowDownIcon
  },
  props: {
    placeholder: {
      type: String,
      required: true
    },
    options: {
      type: Array,
      required: true
    }
  },
  directives: {
    ClickOutsideDirective
  },
  data () {
    return {
      showOptions: false
    }
  },
  methods: {
    toggleOptions() {
      this.showOptions = !this.showOptions
    },
    hideOptions() {
      this.showOptions = false;
    }
  }
}
</script>

<style scoped lang="scss">
@import '../assets/mixin';

.select {
  @include flex(row, space-between, center);
  height: 40px;
  box-sizing: border-box;
  padding: 8px;
  border: solid 1px black;
  border-radius: 2px;
  cursor: pointer;
}

.options {
  position: relative;
  top: -40px;
  background: white;
  border: solid 1px black;
  border-radius: 2px;

  .option {
    @include flex(row, flex-start, center);
    height: 40px;
    box-sizing: border-box;
    padding: 8px;
    cursor: pointer;

    &:hover {
      background: lightgrey;
    }
  }

}
</style>