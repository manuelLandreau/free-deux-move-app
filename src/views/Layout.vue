<template>
    <div style="min-height: calc(100vh - 72px)">
        <Header />
        <div class="container">
            <slot />
        </div>
    </div>
    <hr />
    <footer class="pb-3 text-center">Test Free2move - Manuel Landreau</footer>
</template>

<script>
import Header from '@/components/Header.vue'

export default {
    components: {
        Header
    }
}
</script>
