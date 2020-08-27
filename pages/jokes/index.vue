<template>
    <div>
        <!-- aniun pagdawat og emit sa components, handle by a method -->
        <SearchJokes v-on:search-text="searchText" />

        <!-- aniun pagpasa og data sa props sa components -->
        <Joke v-for="joke in jokes" :key="joke.id" :id="joke.id"  :joke="joke.joke" />
    </div>
</template>
<script>
import axios from 'axios';
import Joke from '../../components/Joke';
import SearchJokes from '../../components/SearchJokes';

export default {
    components:{
        Joke, 
        SearchJokes
    },

    data(){
        return{
            jokes: [],
        }
    }, 
    created(){
        const config = {
            headers: {
                'Accept': 'application/json',
            }
        }

        try{
            axios
            .get("https://icanhazdadjoke.com/search", config)
            .then( res=>{
                // console.log(res.data);
                this.jokes = res.data.results;
            })
        }catch(err){
            console.log(err);
        }
    },
    head() {
        return {
            title: 'Welcome',
            meta: [{
                hid: 'description',
                name: 'description',
                content: 'Best place to cry'
            }]
        }
    },

    methods : {
        searchText(text){
            console.log(text);
            const config = {
                headers: {
                    'Accept': 'application/json',
                }
            }
            
            try{
                axios
                .get("https://icanhazdadjoke.com/search?term="+ text, config)
                .then( res=>{
                    // console.log(res.data);
                    this.jokes = res.data.results;
                })
            }catch(err){
                console.log(err);
            }
        }
    }
}
</script>
<style scoped>

</style>