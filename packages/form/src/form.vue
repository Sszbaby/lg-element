<template>
  <form action="">
    <slot></slot>
  </form>
</template>

<script>
export default {
  name: 'LgForm',
  provide () {
    return {
      form: this
    }
  },
  props: {
    model: {
      type: Object
    },
    rules: {
      type: Object
    }
  },
  methods: {
    validate (cd) {
    //  const tasks = this.$children
    //   .filter(child => child.prop)
    //   .map(child => child.validate())
    const findChild = child => {
        while (child) {
          if (child.$options.name === 'LgFormItem'){
            break
          } else {
            child = child.$children
          }
        }
        return child
      } 
    const tasks = this.$children.map(child => findChild(child))
      .filter(child => child.prop)
      .map(child => child.validate())
      Promise.all(tasks)
        .then(() => cd(true))
        .catch(() => cd(false))
    }
  }
}
</script>

<style>

</style>