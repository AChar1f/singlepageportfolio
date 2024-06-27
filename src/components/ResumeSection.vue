<template>
    <div class="container">
        <div class="row">
            <h2 class="display-2">Skills</h2>
        </div>
        <div class="row">
            <Card v-for="(skill, id) in skills" :key="id">
                <template #cardHeader>
                    <img loading="lazy" class="img-fluid" :src="skill.img_url" :alt="skill.skillName">
                </template>
                <template #cardBody>
                    <h5>{{ skill.skillName }}</h5>
                    <p>{{ skill.proficiency }}</p>
                </template>
            </Card>
        </div>
        <div class="row">
            <div class="col" v-for="(xp, id) in Experience" :key="id">
                <h4 v-for="role in jobTitle" :key="role.index"><span>{{ jobTitle?.role }}</span></h4>
                <h4>{{ xp.location }}</h4>
                <h5>{{ xp.duration }}</h5>
                <p>{{ xp.description }}</p>
            </div>
            <div class="col" v-for="(edu, id) in Education" :key="id">
                <h4>{{ edu.schoolName }} {{ edu.location }}</h4>
                <h5>{{ edu.educationLevel }}</h5>
                <h5>{{ edu.duration }}</h5>
                <h6>{{ edu.qualification }}</h6>
            </div>
        </div>
    </div>
</template>

<script setup>
import { computed, onMounted } from 'vue'
import { useStore } from 'vuex'
import Card from './Card.vue'


const store = useStore()
const jobTitle = computed(() => store.state.jobTitle)
const Experience = computed(() => store.state.Experience)
const Education = computed(() => store.state.Education)
const skills = computed(() => store.state.Skills)

onMounted(() =>{
    store.dispatch('fetchSkills', 'fetchEducation', 'fetchExperience', 'fetchJobTitle')
})
</script>

<style>
    
</style>