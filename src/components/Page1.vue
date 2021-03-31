<template>
    <div>
        <h1>Les articles de blog</h1>
        <hr>

        <ul>
            <li v-for="(article, index) in allArticles" :key="index">
                <!-- dès qu'on clique sur un article on redirige
                le lien vers l'index 
                (+1 pour afficher de 1 à 100 articles au lieu de 0 à 99)-->
                <router-link :to="`/blogPost/${index + 1}`">
                    <div class="card m-2">
                        <h3>{{ article.title }}</h3>
                    </div>
                </router-link>
            </li>
        </ul>
    </div>
</template>

<script>

import axios from 'axios'
export default {
    name: 'Page1',
    data() {
        return {
            allArticles: []
        }
    },
    // quand le composant est crée
    created() {
        axios
        .get('https://jsonplaceholder.typicode.com/posts')
        .then(reponse => {
            // console.log(reponse)
            for(const blogPost of reponse.data) {
                //on enregistre chaque ligne de reponse 
                //dans notre tableau
                this.allArticles.push(blogPost);

            }
        })
    }
}
</script>

<style scoped>

</style>