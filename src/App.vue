<template>
    <Layout>
        <router-view />
    </Layout>
</template>

<style lang="scss">
@import 'assets/scss/styles.scss';
</style>
<script>
import Layout from './views/Layout'
export default {
    components: { Layout }
}
</script>
