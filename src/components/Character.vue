<template>
    <div class="col-12 col-sm-6 col-md-4 col-lg-3 p-4">
        <div class="card">
            <img :src="imgUrl" class="card-img-top" :alt="title" />
            <div class="card-body">
                <h5 class="card-title">{{ title }}</h5>
                <p class="card-text">{{ content }}</p>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        imgUrl: String,
        title: String,
        content: String
    }
}
</script>
