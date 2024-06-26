<template>
    <footer class="container-fluid">
        <div class="row">
            <p class="lead">Abdurahamaan's Portfolio
                <span>&copy;{{ cYear }}</span>
            </p>
        </div>
    </footer>
</template>

<script>
export default {
    name: 'FooterComp',
    data() {
        return {
            cYear : new Date().getUTCFullYear()
        }
    }
}
</script>

<style scoped>
    .container-fluid {
        color: whitesmoke;
        border-top: 4px solid #A29D95;
        background-image: linear-gradient(180deg, black 50%,#232323)
    }
</style>