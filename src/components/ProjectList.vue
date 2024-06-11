<template>
    <div>
        <div class="container">
            <div class="row d-flex flex-wrap">
                <div class="col-4" v-for="project in projects" :key="project.id">
                    <ProjectCard :projectInfo="project"></ProjectCard>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios';
import ProjectCard from './ProjectCard.vue';
export default {
    name: 'ProjectList',
    data() {
        return {
            projects: []
        };
    },
    components: {
        ProjectCard
    },
    methods: {
        getProjectsFromApi() {
            // Call API to get projects
            axios.get('http://127.0.0.1:8000/api/projects')
                .then((response) => {
                    this.projects = response.data.results;
                });
        }
    },
    mounted() {
        this.getProjectsFromApi();
    }
}
</script>

<style lang="scss" scoped></style>