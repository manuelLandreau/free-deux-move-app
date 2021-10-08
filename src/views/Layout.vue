<template>
    <div>
        <Header />
        <div class="container">
            <slot />
        </div>
        <footer>Test Free2move - Manuel Landreau</footer>
    </div>
</template>

<script>
import Header from '@/components/Header.vue'

export default {
    components: {
        Header
    }
}
</script>
