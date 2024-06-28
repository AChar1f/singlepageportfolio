<template>
    <div class="container XP">
        <div class="row">
            <h4 class="display-4">
                Experience
            </h4>
        </div>
        <div class="row">
            <div class="col" v-for="(xp, id) in Experience" :key="id">
                <h4 v-for="role in jobTitle" :key="role.index"><span>{{ jobTitle?.role }}</span></h4>
                <h4>{{ xp.location }}</h4>
                <h5>{{ xp.duration }}</h5>
                <p>{{ xp.description }}</p>
            </div>
        </div>    
    </div>
</template>

<script setup>
import { computed, onMounted } from 'vue'
import { useStore } from 'vuex'


const store = useStore()
const Experience = computed(() => store.state.experience)
onMounted(() => store.dispatch('fetchExperience'))
</script>

<style scoped>
    .XP{
        border: 3px solid white;
    }
</style>