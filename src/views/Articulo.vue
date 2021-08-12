<template>
  <Titulo texto="Ruta con Parametros" />
  <h3>{{ articulo.title }}</h3>
  <p>{{ articulo.body }}</p>
</template>

<script>
import Titulo from '../components/Titulo.vue'
export default {
    name: 'Articulo',
    components: {
        Titulo
    },
    data() {
        return {
            articulo: {}
        }
    },
    methods: {
        async consumirAPI() {
            try {
                const data = await fetch(`https://jsonplaceholder.typicode.com/posts/${ this.$route.params.id }`)
                const response = await data.json()
                this.articulo = response
            } catch (error) {
                console.error(error)
            }
        }
    },
    created () {
        this.consumirAPI();
    },
}
</script>

