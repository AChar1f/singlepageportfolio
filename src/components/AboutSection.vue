<template>
    <div class="container">
        <div class="row  text align-items-center">
            <h2 class="display-2">About</h2>
            <div v-if="about?.length" class="col">
                <img src="https://achar1f.github.io/projectimages/images/me.png" loading="lazy" class="img-fluid rounded-pill"/>
                <p>
                {{ about[0]?.part1 }}
                </p>
            </div>
        </div>
        
    </div>
</template>

<script setup>
import { computed, onMounted } from 'vue'
import { useStore } from 'vuex'

const store = useStore()
const about = computed(() => store.state.about)

onMounted(() => {
    store.dispatch('fetchAbout')
})
</script>

<style scoped>

</style>