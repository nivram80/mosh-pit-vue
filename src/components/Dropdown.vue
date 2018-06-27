<template>
    <div class="dropdown">
        <div class="input">{{label}}</div>
        <div class="options">
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
  export default {
    name: "Dropdown",
    props: {
      label: {
        type: String,
        required: true
      },
      options: {
        type: Array,
        required: true
      }
    }
  }
</script>

<style scoped>

</style>