<template>
  <button @click='onClick()'>{{ text }}</button>
</template>

<script>
export default {
  name: 'Button',
  props: {
    text: {
      type: String,
      default: 'default',
    },
  },
  methods: {
    onClick: () => {
      this.$emit('buttonClick')
    }
  }
}

</script>
