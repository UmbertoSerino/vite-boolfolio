<script>
import axios from 'axios';
export default {
    name: 'AppMain',
    data() {
        return {
            projects: [],
        }
    },
    methods: {
        getProjects() {
            axios.get('http://127.0.0.1:8000/api/projects', {
                params: {
                }
            })
                .then((response) => {
                    console.log(response.data.result.data);
                    this.projects = response.data.result.data;

                })
                .catch(function (error) {
                    console.log(error);
                })
        }
    },

    created() {
        this.getProjects();
    }
}
</script>
<template>
    <main class="container">
        <h1 class="text-center">
            Main
        </h1>
        <div class="row">
            <div class="col-4" v-for="project in projects" :key="project.id">
                <div class="card" style="width: 18rem;">
                    <div class="card-body">
                        <h5 class="card-title">Titolo: {{ project.title }}</h5>
                        <p class="card-text"><strong>Descrizione: </strong>{{ project.description }}</p>
                        <p class="card-text"><strong>Data: </strong>{{ project.date }}</p>
                        <p class="card-text"><strong>Autore: </strong>{{ project.user.name }}</p>
                        <p class="card-text"><strong>Tipo di Tecnologia: </strong>{{ project.type.name }}</p>
                        <p class="card-text"><strong>Tecnologie: </strong></p>
                        <ul>
                            <li v-for="technology in project.technologies" :key="technology.id">{{ technology.name }}</li>
                        </ul>
                        <a :href="project.url" class="btn btn-primary">Go somewhere</a>
                    </div>
                </div>
            </div>
        </div>
    </main>
</template>

<style lang="scss" scoped>
@use '../style/partials/mixins' as*;
@use '../style/partials/variables' as*;
</style>