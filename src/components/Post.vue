<template>
    <div>
        <h1>Le post numéro {{ id }}</h1>
        <div>
            <h2>{{ articleUnique.title }}</h2>
            <br>
            <p>{{ articleUnique.body }}</p>
        </div>
    </div>
</template>

<script>
import axios from 'axios'

export default {
    name: 'Post',
    data() {
        return {
            id: this.$route.params.id,
            articleUnique: []
        }
    },
    // quand le composant est monté dans le DOM
    mounted() {
        axios
        // on fait notre appel API seulement pour
        // l'article sur lequel on va cliquer dans notre liste
        .get(`https://jsonplaceholder.typicode.com/posts/${this.id}`)
        .then(reponse => {
            // console.log(reponse)
            this.articleUnique = reponse.data
        })
    }
}
</script>

<style scoped>

</style>