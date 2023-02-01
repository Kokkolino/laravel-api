<template>
    <div class="container-lg row flex justify-content-between mx-auto gap-5">

        <PostCard
        v-for="item in posts"
        :key="item.id"
        :post="item"
        :load="loading"
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
            loading: false
        }
    },

    // methods
    methods: {
        getPosts() {
            this.loading = true;
            axios.get('http://127.0.0.1:8000/api/posts')
            .then(res=>{
                this.posts = res.data;
            }).catch(err => {
                console.log(err)
            }).then(() => {
                this.loading = false
            })
        }
    },

    // mounted
    mounted() {
        this.getPosts();
    }
}
</script>
