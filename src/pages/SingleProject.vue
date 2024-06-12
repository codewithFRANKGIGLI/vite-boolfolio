<script>
import axios from 'axios';

export default {
    name: 'SingleProject',
    data() {
        return {
            project: null
        };
    },
    methods: {
        getProjectDetails() {
            axios.get(`http://127.0.0.1:8000/api/projects/${this.$route.params.slug}`)
                .then((response) => {
                    this.project = response.data.project;
                });
        }
    },
    mounted() {
        this.getProjectDetails();
    }
}
</script>

<template>
    <div class="container">
        <div v-if="project">
            <h1>{{ project.name }}</h1>

            <div v-if="project.cover_img">
                <img :src="`http://127.0.0.1:8000/storage/${project.cover_img}`" :alt="project.name" style="width: 20rem;">
            </div>

            <p v-if="project.summary">
                {{ project.summary }}
            </p>
        </div>
    </div>
</template>