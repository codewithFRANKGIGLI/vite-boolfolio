<template>


    <!-- cards -->
    <div class="card" style="width: 15rem;">
        <div class="card-body">
            <!-- <img src="{{ projectInfo.cover_img }}" alt=""> -->
            <h5 class="card-title">{{ projectInfo.name }}</h5>
            <div v-if="projectInfo.type">
                <strong>Type</strong>:
                {{ projectInfo.type.name }}
            </div>
            <p v-if="projectInfo.summary" class="card-text">{{ projectInfo.summary }}</p>
            <!-- <a href="#" class="btn btn-primary">Go somewhere</a> -->
        </div>
    </div>

</template>

<script>
export default {
    name: 'ProjectCard',
    props: {
        projectInfo: Object
    }
}
</script>

<style lang="scss" scoped></style>