<template>
    <div class="container">
        <div class="row gap-3 justify-content-center">
            <Card v-for="(skill, id) in skills" :key="id">
                <template #cardHeader>
                    <img loading="lazy" class="img-fluid" :src="skill.img_url" :alt="skill.skillName">
                </template>
                <template #cardBody>
                    <h5>{{ skill.skillName }}</h5>
                </template>
            </Card>
        </div>
    </div>
</template>

<script setup>
import { computed, onMounted } from 'vue'
import { useStore } from 'vuex'
import Card from './Card.vue'

const store = useStore()
const skills = computed(() => store.state.skills)

onMounted(() => store.dispatch('fetchSkills'))
</script>
    
