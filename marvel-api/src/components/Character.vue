<template lang="html">
    <div>
        <div class=flex-container>

            <div class="flex" v-for="char in character">
                <h3>{{char.name}}</h3>
                <p>{{char.description}}</p>
            </div>

            <div class="flex2">
                <img :src="url" class="img">
            </div>
                

        
        </div>
        <router-link to="/">
             <button type="button" name="button" class="btn-voltar">Voltar</button>       
        </router-link>
        
    </div>    
</template>

<script>
import {public_key} from '../marvel'
import axios from 'axios'
import {mapState} from 'vuex'
export default {
    name: 'Character',

    data(){
        return{
            url: '',
            size: 'standart_large.jpg'
        }
    },

    mounted(){
        this.$store.dispatch('getCharacter', this.$route.params.id)

        this.getImage()
    },

    computed: {
        ...mapState({
            character: state => state.character,
            preUrl: state => state.url
        })
    },

    methods: {
        getImage: function () {
            this.url = `${this.preUrl}${this.size}`;
        }
    }
}
</script>

<style lang="css">

    .flex-container{
        margin: 75px;
        text-align: center;
        display: flex;
        align-items: center;
        justify-content: center;
    }

    .flex{
        flex: 50%;

    }

    .flex2{
        flex: 50%;
    }

    .img{
        width: 35%;
        border-radius: 10px;
    }

    .btn-voltar{
        width: 85px;
        height: 35px;
        border-radius: 10px;
        border-width: 1px;
        background-color: transparent;
        cursor: pointer;
    }



</style>


