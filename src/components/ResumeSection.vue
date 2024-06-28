<template>
    <div class="container">
        <div class="row">
            <h2 class="display-2">
                Resume
            </h2>
        </div>
        <div class="row">
            <h4 class="display-4">Skills</h4>
        </div>
        <div class="row">
            <Skills/>
        </div>
        <div class="row mt-3">
            <Experience/>
        </div>
        <div class="row mt-3">
            <Education/>
        </div>
    </div>
</template>

<script>
import Skills from './SkillsComp.vue'
import Education from './EducationComp.vue'
import Experience from './ExperienceComp.vue'

export default{
name: 'ResumeSection',
components: {
    Experience, Education, Skills
}
}
</script>

<style>
    
</style>