<template>
    <div style="">
        <Header />
        <div class="container">
            <slot />
        </div>
    </div>
    <hr />
    <footer class="pb-3 text-center">Test - Manuel Landreau</footer>
</template>

<script>
import Header from '@/components/Header.vue'

export default {
    components: {
        Header
    }
}
</script>
