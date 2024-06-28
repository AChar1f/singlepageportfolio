<template>
    <div class="container">
        <div class="row pt-5">
            <h2 class="display-2">Projects</h2>
        </div>
        <div class="row gap-3 mb-3 justify-content-center">
            <Card v-for="(project, id) in projects" :key="id">
                <template #cardHeader>
                    <img class="img-fluid" :src="project.img_url" :alt="project.projectName" loading="lazy">
                </template>
                <template #cardBody>
                    <h5>{{ project.projectName }}</h5>
                    <p>{{ project.description }}</p>
                    <a :href="project.gitHub" target="_blank"><button type="button" class="btn">Github</button></a>
                    <a :href="project.vercel" target="_blank"><button type ="button" class="btn">Vercel</button></a>
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
        background-color: darkslategrey;
        color: whitesmoke;
    }
</style>