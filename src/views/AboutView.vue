<script>
  export default {
    mounted() {
      this.makeMetricsCall()
    },
    data () {

    },
    methods: {
      async makeMetricsCall() {
        let ref = this;
        ref.cs_params = {
          "integration_id": "lj3a30rjw9",
          "publisher": 'demo',
          "offer": 'demo',
          "sub_id": 'demo',
          "token": 'demotoken'
        };

        // Attach cs_param to the window object as a constant
        Object.defineProperty(window, 'cs_params', {
          value: ref.cs_params
        });

        // Load the external script
        const script = document.createElement('script');
        script.src = 'https://static.24metrics.com/js/index.js';
        document.head.appendChild(script);
      }
    }
  }
</script>

<template>
  <div>
    <h1>redirection page</h1>
  </div>
</template>

<style scoped>

</style>