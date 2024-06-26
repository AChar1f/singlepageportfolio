<template>
    <div class="container">
        <div class="row">
            <div class="col">
                <img src="https://achar1f.github.io/projectimages/images/me.png" alt="profile" loading="lazy" class="img-fluid">
            </div>
            <div class="col">
                <div id="details">
                    <h1 class="display-1">Abdurahmaan Charif</h1>
                    <span>{{ jobTitle[0].role }}</span>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>
import {computed, onMounted} from 'vue'

const jobTitle = computed(() => this.$store.state.jobTitle)
onMounted(() => {
    this.$store.dispatch('fetchJobTitle')
})
// export default {  // used in options currently composition is running
//     name: 'LandingSection'
// }
</script>

<style scoped>
    
</style>

