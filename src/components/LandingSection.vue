<template>
  <div class="container">
    <div class="row vh-100 align-items-center">
      <div class="col">
        <img
          src="https://achar1f.github.io/projectimages/images/me.png"
          alt="profile"
          loading="lazy"
          class="img-fluid rounded-2"
        />
      </div>
      <div class="col">
        <div id="details">
          <h2 class="display-2">Abdurahmaan Charif</h2>
          <p v-if="title">
            <span>The {{ title }}</span>
          </p>
          <Spinner v-else/>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import Spinner from './Spinner.vue'
import { computed, onMounted, ref } from "vue";
import { useStore } from "vuex";
import Swal from "sweetalert2/dist/sweetalert2";

const store = useStore();
const jobTitle = computed(() => store.state.jobTitle);
const title = ref("Junior Developer");
const cnt = ref(-1);

function repeat() {
  try {
    if (cnt.value == jobTitle.value?.length) cnt.value = 0;
    title.value = jobTitle.value?.at(cnt.value)?.role;
    setTimeout(repeat, 2000);
    cnt.value++;
  } catch (e) {
    //insert sweet alert
    Swal.fire({
      title: "Error",
      text: "Failed to fetch about data",
      icon: "error",
      timer: 2000,
    });
  }
}

onMounted(() => {
  store.dispatch("fetchJobTitle");
  repeat();
});
//ref allows you to make use of a primitive data type in comp ai
//reactive allows you to make use of mutative data types in comp ai
// export default {  // used in options currently composition is running
//     name: 'LandingSection'
// }
</script>

<style scoped>
</style>
