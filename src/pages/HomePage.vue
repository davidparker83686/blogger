<template>
  <div class="row">
    <Blog v-for="blog in state.blogs" :key="blog.id" :blog="blog" />
    <span> blogs go here</span>
  </div>
</template>

<script>
import { onMounted, reactive, computed } from 'vue'
import { blogsService } from '../services/BlogsService.js'
import { AppState } from '../AppState'
import { logger } from '../utils/Logger'

export default {
  name: 'Home',
  setup() {
    const state = reactive({
      blogs: computed(() => AppState.blogs)
    })
    onMounted(async() => {
      try {
        await blogsService.getAll()
      } catch (error) {
        logger.error(error)
      }
    })

    return {
      state
    }
  }
}
</script>

<style scoped lang="scss">
.home{
  text-align: center;
  user-select: none;
  > img{
    height: 200px;
    width: 200px;
  }
}
</style>
