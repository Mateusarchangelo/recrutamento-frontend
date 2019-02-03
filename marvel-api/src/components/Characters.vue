<template lang="html">
    <div>
        <div class="card-container">
            <div class="card" v-for="character in characters">
                <h3>{{character.name}}</h3>
                <router-link :to="{name: 'character', params: {id: character.id} }">
                    <button type="button" name="button" class="btn">Ver</button>
                </router-link>
            </div>  
        </div>
    </div>
        
</template>

<script>
import { public_key, secret_key } from '../marvel'
import axios from 'axios'
import {mapState} from 'vuex'
export default {
    name: 'Characters',

    mounted(){
        
        this.$store.dispatch('getCharacters')
        console.log(this.characters)
    },

    computed:{
    ...mapState({
        characters: state => state.characters
    })
    
    },

    methods:{
        
            
    }
  }
</script>

<style lang="css">
    .card-container{
        margin-left: 500px;
        display: grid;
        grid-template-columns: 250px 250px 250px;
        grid-gap: 45px;
    }

    .card{
        text-align: center;
        background-color: #DCDCDC;
        min-height: 200px;
        border-radius: 10px;
    }

    .btn{
        padding: 5px;
        margin-top: 70px;
        border-radius: 25px;
        border-width: 1px;
        width: 110px;
        background-color: transparent;
        color: black;
        cursor: pointer;
        border-color: black;
    }


</style>

