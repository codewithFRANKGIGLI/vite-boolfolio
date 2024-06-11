<template>
    <div>
        <div class="container">
            <div class="row flex-wrap justify-content-between">
                <div class="col-4" v-for="project in projects" :key="project.id">
                    <ProjectCard :projectInfo="project"></ProjectCard>
                </div>
            </div>
            <nav aria-label="Page navigation example">
            <ul class="pagination">
                <li v-if="prevPageUrl" class="page-item">
                    <a class="page-link" @click="getProjects(currentPage - 1)">Previous</a>
                </li>
                <li v-if="nextPageUrl" class="page-item">
                    <a class="page-link" @click="getProjects(currentPage + 1)">Next</a>
                </li>
            </ul>
        </nav>
        </div>
    </div>
</template>

<script>
import axios from 'axios';
import ProjectCard from '../components/ProjectCard.vue';
export default {
    name: 'ProjectList',
    components: {
        ProjectCard
    },
    data() {
        return {
            currentPage: 1,
            prevPageUrl: null,
            nextPageUrl: null,
            projects: []
        };
    },
    methods: {
        getProjects(pageNumber) {
            axios.get('http://127.0.0.1:8000/api/projects', {
                params: {
                    page: pageNumber
                }
            })
            .then((response) => {
                this.projects = response.data.results.data;
                this.currentPage = response.data.results.current_page;
                this.prevPageUrl = response.data.results.prev_page_url;
                this.nextPageUrl = response.data.results.next_page_url;
            });
        }
    },
    mounted() {
        this.getProjects(this.currentPage);
    }
}
</script>

<style lang="scss" scoped></style>