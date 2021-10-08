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
        await this.getPage()
    },
    methods: {
        async getPage(p = 1) {
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
