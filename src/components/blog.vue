<template>
  <div class=" card col-md-3" v-if="blog.creator">
    <router-link :to="{name: 'BlogDetails', params: {id: blog.id}}">
      <h3>{{ blog.title }}</h3>
      <h5>
        {{ blog.creator.name }}
      </h5>
    </router-link>
  </div>
</template>

<script>
export default {
  name: 'Blog',
  props: {
    blog: {
      type: Object,
      require: true
    }
  },
  setup() {
    return {}
  }

}
</script>

<style lang="scss">

</style>
