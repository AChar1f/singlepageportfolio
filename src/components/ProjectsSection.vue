<template>
    <div class="container-fluid">
        <div class="row">
            <h2 class="display-2">Projects</h2>
        </div>
        <div class="row gap-3 mb-3 justify-content-start">
            <Card v-for="(project, id) in projects" :key="id">
                <template #cardHeader>
                    <img class="img-fluid" :src="project.img_url" :alt="project.projectName" loading="lazy">
                </template>
                <template #cardBody>
                    <h5>{{ project.projectName }}</h5>
                    <p>{{ project.description }}</p>
                    <a :href="project.gitHub"><button type="button" class="btn btn-success">Github</button></a>
                    <a :href="project.vercel"><button type ="button" class="btn btn-success">Vercel</button></a>
                </template>
            </Card>
        </div>
    </div>
</template>

<script setup>
import  Card from './Card.vue'
import { computed, onMounted} from 'vue'
import { useStore } from 'vuex'

const store = useStore()
const projects = computed(() => store.state.projects) 

onMounted(() => {
    store.dispatch('fetchProjects')
})
</script>

<style scoped>
    .btn{
        margin-inline: 0.5rem;
    }
</style>