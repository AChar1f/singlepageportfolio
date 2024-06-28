<template>
    <div class="container Edu">
        <div class="row">
        <h4 class="display-4">Education</h4>
    </div>
        <div class="row">
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

const store = useStore()
const Education = computed(() => store.state.education)
onMounted(() => store.dispatch('fetchEducation'))
</script>

<style scoped>
    .Edu{
        border: 3px solid white;
    }
</style>