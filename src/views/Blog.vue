<template>
  <Titulo texto="Titulo de mi blog"/>
  <div v-for="item in arrayBlog" :key="item.id">
      <router-link :to="`/blog/${item.id}`">
          {{ item.title }}
      </router-link>
      
  </div>
</template>

<script>
import Titulo from '../components/Titulo.vue'

export default {
    name: 'Blog',
    components: {
        Titulo
    },
    data() {
        return {
            arrayBlog: []
        }
    },
    methods: {
        async consumirAPI() {
            try {
                const data = await fetch('https://jsonplaceholder.typicode.com/posts')
                const array = await data.json()
                this.arrayBlog = array
            } catch (error) {
                console.error(error)
            }
        }
    },
    created () {
        this.consumirAPI()
    },
}
</script>

<style>

</style>