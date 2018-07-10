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
    name: "DropdownSelect",
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
  @import '../../assets/mixin';

  .select {
    @include flex(row, space-between, center);
    height: 40px;
    box-sizing: border-box;
    padding: 8px;
    border: solid 1px black;
    border-radius: 2px;
    cursor: pointer;

    .placeholder {
      color: lightgray;
    }

    .model {
      color: black;
    }
  }
</style>