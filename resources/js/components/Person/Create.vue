<template>
    <div class="w-25">
        <div class="mb-3">
            <input type="text" v-model="name" placeholder="name" class="form-control">
        </div>
        <div class="mb-3">
            <input type="number" v-model="age" placeholder="age" class="form-control">
        </div>
        <div class="mb-3">
            <input type="text" v-model="job" placeholder="job" class="form-control">
        </div>
        <div class="mb-3">
            <input :disabled="!isDisabled" @click.prevent="store" type="submut" value="Add" class="btn btn-primary">
        </div>
    </div>

</template>

<script>

import axios from 'axios';

    export default {
        name: "Create",

        data(){
            return {
                name: null,
                age:null,
                job:null,
            }
        },

        destroy(){
            this.someLog()
        },


        methods: {
            store(){
                axios.post('/api/people', {name: this.name, age:this.age, job:this.job})
                .then(res =>{
                    this.$router.push({name:'person.index'})
                })
            },
            someLog(){
                console.log(1111);
            }


        },
        computed:{
            isDisabled(){
                return this.name && this.age && this.job
            }
        }
    }
</script>
<style scoped>

</style>
