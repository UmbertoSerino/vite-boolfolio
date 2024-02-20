<script>
import axios from 'axios';
export default {
    name: 'AppMain',
    data() {
        return {

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
    </main>
</template>
<style lang="scss" scoped>
@use '../style/partials/mixins' as*;
@use '../style/partials/variables' as*;
</style>