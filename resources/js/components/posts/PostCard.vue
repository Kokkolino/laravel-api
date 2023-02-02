<template>
<div class="card col-5 pt-3 mb-5">
    <div v-if="isLoading" class="card" aria-hidden="true">
        <img src="..." class="card-img-top" alt="...">
        <div class="card-body">
            <h5 class="card-title placeholder-glow">
                <span class="placeholder col-6"></span>
            </h5>
            <p class="card-text placeholder-glow">
                <span class="placeholder col-7"></span>
                <span class="placeholder col-4"></span>
                <span class="placeholder col-4"></span>
                <span class="placeholder col-6"></span>
                <span class="placeholder col-8"></span>
            </p>
            <a href="#" tabindex="-1" class="btn btn-primary disabled placeholder col-6"></a>
        </div>
    </div>

    <div v-else>
            <!-- {{-- image --}} -->
            <img v-if="post.image !== null" :src="require(`../../../../public/storage/${post.image}`)" class="card-img-top" alt="...">
            <img v-else src="../../../../public/storage/post_images/no-image-available.png" class="card-img-top" alt="...">

            <div class="card-body">
                <!-- {{-- title --}} -->
                <h5 class="card-title">{{post.title}}</h5>
                <!-- {{-- description --}} -->
                <p class="card-text">{{post.description}}</p>
                <!-- {{-- category --}} -->
                <p v-if="post.category !== null" class="card-text">categoria: {{post.category['category']}}</p>

                <!-- {{-- tags --}} -->
                <p v-if="post.tags.length !== 0" class="card-text">
                    tags:
                    <a v-for="tag in post.tags" href="#">
                        #{{tag.name}}
                    </a>
                </p>
                <!-- {{-- go to post --}} -->
                <a href="#" class="btn btn-primary mb-1">Go to post</a>
            </div>
    </div>
</div>

</template>

<script>

export default{
    name: 'PostCard',
    props: {
        post: Object,
        isLoading: Boolean
    },

    data(){
        return{

        }
    },

    methods: {

    },
    mounted(){

    }
}
</script>
