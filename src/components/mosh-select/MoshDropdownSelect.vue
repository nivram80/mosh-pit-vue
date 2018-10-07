<template>
  <div
    class="select"
    :id="idHashKey"
    @click="$emit('toggleOptions', idHashKey)"
  >
    <div
      class="placeholder"
      v-show="!model"
    >
      {{placeholder}}
    </div>
    <div
      class="model"
      v-show="model"
    >
      {{model}}
    </div>
    <KeyboardArrowDownIcon/>
  </div>
</template>

<script>
  import KeyboardArrowDownIcon from '@/components/icons/KeyboardArrowDownIcon.vue'

  export default {
    name: "MoshDropdownSelect",
    components: {
      KeyboardArrowDownIcon
    },
    props: {
      placeholder: {
        type: String,
        required: false
      },
      model: {
        type: String,
        required: false
      }
    },
    computed: {
      idHashKey() {
        return Math.floor(Math.random() * 900000000000000)
      }
    }
  }
</script>

<style scoped lang="scss">
  .select {
    @include flex(row, space-between, center);
    height: $select-height;
    @include form-element-block-styles;

    .placeholder {
      color: $input-placeholder-color;
    }

    .model {
      color: $default-font-color;
    }
  }
</style>