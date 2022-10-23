<template>
    <div class="box">
        <div class="container is-max-desktop">
            <form @submit.prevent="updateName">
                <div class="columns is-mobile is-centered">
                    <div class="column is-four-fifths"><div class="field">
                        <input class="input" type="text" placeholder="Search" v-model="name"> 
                    </div>
                </div>
                </div>
            </form>
        </div>
    </div>
</template>

<script>
    export default{
        data(){
            return{
                name : ''
            }
        },
        methods : {
            updateName(){
                this.$emit('searchNow',this.name);
                this.name='';
            }
        }
    }
</script>