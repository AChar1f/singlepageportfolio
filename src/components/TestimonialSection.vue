<template>
    <div class="container-fluid">
        <div class="row">
            <h2 class="display-2">Testimonials</h2>
        </div>
        <div class="row justify-content-center gap-3 mb-3">
            <Card v-for="(testimonial, id) in testimonials" :key="id">
                <template #cardHeader>
                    <img class="img-fluid" :src="testimonial.img_url" :alt="testimonial.name" loading="lazy">
                </template>
                <template #cardBody>
                    <h5>{{ testimonial.name }}</h5>
                    <h6>{{ testimonial.affiliation }}</h6>
                    <p>{{ testimonial.quote }}</p>
                </template>
            </Card>
        </div>
    </div>
</template>

<script setup>
import { computed, onMounted} from 'vue'
import { useStore } from 'vuex'
import Card from './Card.vue'

const store = useStore()
const testimonials = computed(() => store.state.testimonials) 

onMounted(() => {
    store.dispatch('fetchTestimonials')
})
</script>

<style scoped>

</style>