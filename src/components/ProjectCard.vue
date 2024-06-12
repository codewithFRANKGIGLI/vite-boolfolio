<template>


    <!-- cards -->
    <div class="card my-3" style="height: 18rem;">
        <div class="card-body d-flex flex-column justify-content-between flex-wrap">
            <img :src="`http://127.0.0.1:8000/storage/${projectInfo.cover_img}`" :alt="projectInfo.name" style="height: 5rem; width: fit-content;">
            <h5 class="card-title">{{ projectInfo.name }}</h5>
            <div v-if="projectInfo.type">
                <strong>Type</strong>:
                {{ projectInfo.type.name }}
            </div>
            <p v-if="projectInfo.summary" class="card-text">{{ truncateText(projectInfo.summary) }}</p>
            <router-link :to="{ name: 'single-project', params: {slug: projectInfo.slug } }" class="btn btn-primary">View more</router-link>
        </div>
    </div>

</template>

<script>
export default {
    name: 'ProjectCard',
    props: {
        projectInfo: Object
    },
    methods: {
        truncateText(text) {
            if (text.length > 100) {
                return text.substring(0, 100) + '...';
            }
            return text;
        }
    }
}
</script>

<style lang="scss" scoped></style>