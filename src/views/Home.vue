<template>
    <div v-if="loading" class="mt-5 text-center">
        <div class="spinner-border" role="status">
            <span class="visually-hidden">Loading...</span>
        </div>
    </div>

    <div v-else class="row">
        <Character
            v-for="character in characters"
            :imgUrl="character.thumbnail.path + '.' + character.thumbnail.extension"
            :title="character.name"
            :content="character.description"
            :key="character.id"
        />

        <div class="d-flex flex-row-reverse">
            <nav class="mt-3">
                <ul class="pagination">
                    <li class="page-item" :class="{ disabled: disabledPrevious }">
                        <a class="page-link cursor-pointer" @click="switchPage(+page - 1)" tabindex="-1" :aria-disabled="disabledPrevious">
                            Previous
                        </a>
                    </li>
                    <li v-if="+page === 1" class="page-item active" aria-current="page">
                        <a class="page-link" href="#">1</a>
                    </li>
                    <li v-if="+page > 1" class="page-item cursor-pointer">
                        <a class="page-link" @click="switchPage(+page - 1)">{{ +page - 1 }}</a>
                    </li>
                    <li v-if="+page > 1" class="page-item active" aria-current="page">
                        <a class="page-link" href="#">{{ +page }}</a>
                    </li>
                    <li v-if="+page < total / 20" class="page-item">
                        <a class="page-link cursor-pointer" @click="switchPage(+page + 1)">{{ +page + 1 }}</a>
                    </li>
                    <li v-if="+page < total / 20 && +page === 1" class="page-item">
                        <a class="page-link cursor-pointer" @click="switchPage(+page + 2)">{{ +page + 2 }}</a>
                    </li>
                    <li class="page-item" :class="{ disabled: disabledNext }">
                        <a
                            class="page-link cursor-pointer"
                            @click="switchPage(+page + 1)"
                            :aria-disabled="disabledNext">
                            Next
                        </a>
                    </li>
                </ul>
            </nav>
        </div>
    </div>

    <div v-if="error">{{ error }}</div>
</template>

<script>
import axios from 'axios'
import Character from '@/components/Character'

export default {
    components: {
        Character
    },
    data: () => ({
        characters: [],
        offset: 20,
        total: 0,
        page: 1,
        loading: false,
        error: null
    }),
    async created() {
        await this.getPage(this.$route.params.page || 1)
    },
    computed: {
        disabledPrevious() {
            return +this.page === 1
        },
        disabledNext() {
            return +this.page >= +this.total / 20
        }
    },
    methods: {
        switchPage(p) {
            this.$router.push('/' + p)
            this.getPage(p)
        },
        async getPage(p) {
            this.loading = true
            try {
                const { data } = await axios.get(process.env.VUE_APP_API_URL + '/marvel/' + p)
                this.characters = data.characters
                this.offset = data.offset
                this.total = data.total
                this.page = data.page
                this.loading = false
            } catch (e) {
                this.error = 'something is wrong...'
                this.loading = false
            }
        }
    }
}
</script>

<style scoped>
.cursor-pointer {
    cursor: pointer;
}
</style>
