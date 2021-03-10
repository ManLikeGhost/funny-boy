<template>
  <div>
      <h3>One joke to rule them all</h3> 
      <nuxt-link to="/jokes">To more jokes and beyond</nuxt-link>
      <p>{{ joke }}</p>
      <p>{{ $route.params.id }}</p>
  </div>
</template>

<script>
import axios from 'axios';


export default {
    data() {
        return {
            joke: {}
        }
    },

    async created() {
        const config = {
        headers: {
            'Accept': 'application/json'
        }
        }
        try {
        const res = await axios.get(
            `https://icanhazdadjoke.com/j/${this.$route.params.id}`, 
            config);

            this.joke = res.data.joke;
            
        } catch (err) {
        console.log(err)
        
        }
        
    },
};
</script>

<style>

</style>