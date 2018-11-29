<template>
  <div>
    <head-nav/>
    <p>Agent ID: {{ $route.params.id }}</p>
  </div>
</template>

<script>
  import HeadNav from '~/components/Nav.vue'

  export default {
    components: {
      HeadNav
    }
  }
</script>
