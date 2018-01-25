<template>
  <div class="sourceselection">
    <h4>Select News source</h4>
    <select class="form-control" v-on:change="sourceChanged">
      <option v-bind:value="source.id" v-for="source in sources">{{source.name}}</option>
    </select>
  </div>
</template>

<script>
export default {
  name: 'sourceselection',
  data () {
    return {
      soruces: [],
      soruce: ''
    }
  },
  methods: {
    sourceChanged: function(e) {
      for (var i = 0; i < this.soruces.length; i++) {
        if(this.sources[i].id == e.target.value) {
          this.source = this.sources[i]
        }
        this.soruces[i]
      }
    }
  },
  created: function() {
    this.$http.get('https://newsapi.org/v1/sources?language=en')
      .then(function(response) {
        console.log(response.data.sources);
        this.sources = response.data.sources;
      });
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
