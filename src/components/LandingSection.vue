<template>
    <div class="container">
        <div class="row">
            <div class="col">
                <img src="https://achar1f.github.io/projectimages/images/me.png" alt="profile" loading="lazy" class="img-fluid">
            </div>
            <div class="col">
                <div id="details">
                    <h1 class="display-1">Abdurahmaan Charif</h1>
                    <p v-if="jobTitle?.length"><span>{{ jobTitle[2]?.role }}</span></p>
                    <div v-else class="d-flex justify-content-center">
                    <div class="spinner-border" role="status">
                    </div>
</div>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>
import {computed, onMounted} from 'vue'
import { useStore } from 'vuex'

const store = useStore()
const jobTitle = computed(() => store.state.jobTitle)
onMounted(() => {
    store.dispatch('fetchJobTitle')
})
// export default {  // used in options currently composition is running
//     name: 'LandingSection'
// }
</script>

<style scoped>
    
</style>

