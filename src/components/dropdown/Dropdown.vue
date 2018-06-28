<template>
  <div
    class="dropdown"
    v-click-outside="hideOptions"
  >
    <DropdownSelect :placeholder="placeholder" @toggleOptions="toggleOptions" />
    <DropdownOptions :showOptions="showOptions" :options="options" />
  </div>
</template>

<script>
import { ClickOutsideDirective } from '@/directives/ClickOutsideDirective.js';
import DropdownSelect from '@/components/dropdown/DropdownSelect';
import DropdownOptions from '@/components/dropdown/DropdownOptions.vue';

export default {
  name: "Dropdown",
  components: {
    DropdownSelect,
    DropdownOptions
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
