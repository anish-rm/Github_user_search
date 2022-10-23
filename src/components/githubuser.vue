<template>
    <div>
        <inputField @searchNow="searchName"></inputField>
        <div v-if="card" class="container is-max-desktop">
            <div class="columns is-mobile is-centered">
                <div class="column is-half">
                    <div class="card">
                        <img :src="image.avatar_url" class="card-img-top" alt="...">
                        <div class="card-body">
                            <h5 class="card-title">{{image.name}}</h5>
                            <p class="card-text border-bottom text-dark">Joined in {{year}}</p>
                            <p class="card-text" v-if="image.bio">Bio : {{image.bio}}</p>
                            <p class="card-text" v-if="image.company">Company : {{image.company}}</p>
                            <p class="card-text" v-if="image.location">Location : {{image.location}}</p>
                            <p class="card-text" v-if="image.email">Email : {{image.email}}</p>
                            <p class="card-text">Repositries : {{image.public_repos}}</p>
                            <p><i class="bi bi-people-fill"></i> {{image.followers}} followers <i class="bi bi-dot"></i> {{image.following}} following</p>
                            <a :href="image.html_url" class="btn btn-primary">Github</a>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
    <!-- </div> -->
</template>

<script>
    import inputField from './inputField.vue';
    export default{
        data(){
        return{
            image:[],
            name:'anish-rm',
            names:'',
            date : null,
            year : null,
            card : false
        }
    },
    mounted(){
        // axios
        // .get(`https://api.github.com/users/${this.name}`)
        // .then((res)=> this.image=res.data)
    },
    beforeUpdate(){
        this.date = this.image.created_at
        this.year = (dateFns.format(this.date, 'YYYY'));
    },
    components : {
        inputField
    },
    methods:{
        searchName(n){
            this.name = n;
            this.card=true;
            axios
        .get(`https://api.github.com/users/${this.name}`)
        .then((res)=> this.image=res.data)
        }
    }
    }
</script>

<style scoped>
    @import "https://cdn.jsdelivr.net/npm/bulma@0.9.4/css/bulma.min.css";

</style>