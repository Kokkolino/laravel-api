<template>
    <div class="container-lg row flex justify-content-between mx-auto mt-5 gap-5">

        <PostCard
        v-for="item in posts"
        :key="item.id"
        :post="item"
        :isLoading="isLoading"
        />

    </div>

</template>

<script>
import PostCard from "../components/posts/PostCard.vue"

export default {
    name: "App",

    // components
    components: {
        PostCard
    },

    // data
    data(){
        return{
            posts:[],
            isLoading: false
        }
    },

    // methods
    methods: {
        getPosts() {
            this.isLoading = true;
            axios.get('http://127.0.0.1:8000/api/posts')
            .then(res=>{
                this.posts = res.data.data;
                console.log(this.posts)
            }).catch(err => {
                console.log(err)
            }).then(() => {
                this.isLoading = false
            })
        }
    },

    // mounted
    mounted() {
        this.getPosts();

    }
}
</script>
