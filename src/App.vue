<template>
    <Layout>
        <router-view />
    </Layout>
</template>

<script>
import Layout from './views/Layout'

export default {
    components: { Layout }
}
</script>

<style lang="scss">
@import './assets/scss/styles.scss';
</style>
