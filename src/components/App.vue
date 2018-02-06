<template>
  <div id="app">
    <h3>Got jokes?</h3>
    <button class="btn btn-primary" @click="initJokes">Add Ten Random Jokes</button>
    <button class="btn btn-primary" @click="addJoke">Add Random Joke</button>
    <br>
    <span v-for="type in types">
      <input
      type="checkbox"
      :value="type"
      v-model="checkTypes"

      >
      <label>{{type}}</label>&nbsp;&nbsp;
    </span>
    <br>
    <div class="jokes-columns">
      <Joke
        v-for="(joke, index) in $store.state.jokes"
        v-show="checkTypes.includes(joke.type)"
        :joke="joke"
        :key="index"
        :index="index"
      />
    </div>
  </div>
</template>

<script>
import { mapActions } from 'vuex'
import Joke from './joke.vue'

export default {
  data () {
    return {
      types: ['general', 'knock-knock', 'programming'],
      checkTypes: ['general', 'knock-knock', 'programming']
    }
  },
  methods: mapActions([
    'initJokes',
    'addJoke',
  ]),
  components: {
    Joke
  }
}

</script>
