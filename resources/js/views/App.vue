<template>
    <div class="container-lg row flex justify-content-between mx-auto gap-5">


    </div>

</template>

<script>
  export default {
    name: "App",

    // components
    components: {

    },

    // data
    data(){
        return{
            posts:[],
        }
    },

    // methods
    methods: {
        getPosts() {
            axios.get('http://127.0.0.1:8000/api/posts')
            .then(res=>{
                this.posts = res.data;
            })
        }
    },

    // mounted
    mounted() {
        this.getPosts();
    }
  };
</script>
