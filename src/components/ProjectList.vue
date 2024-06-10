<template>
    <div>
        <div class="container">
            <div class="row">
                <div class="col-md-12">
                    <!-- cards -->
                     <div class="card" v-for="item in items" :key="item.id">
                        
                     </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: "ProjectList"
    }
</script>

<style lang="scss" scoped>

</style>