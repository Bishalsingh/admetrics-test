<template>
  <div>
    <h1>This is page one for fingerprint getting</h1>
  </div>
</template>

<script>
import router from "./../router/index";
  export default {
    data () {
      return {
        vId: ''
      }
    },
    mounted() {
      this.makeMetricsCall()
    },
    methods: {
      async makeMetricsCall() {
        let ref = this;
        this.cs_params = {
          "integration_id": "e1be6hz3oa",
          "publisher": 'demo_demo',
          "sub_id": 'userone1',
          "json": true,
          "redirect": false
        };

        // Attach cs_param to the window object as a constant
        this.scriptProperty = Object.defineProperty(Object.prototype, 'cs_params', {
          value: this.cs_params,
          configurable: true,
          enumerable: false,
          writable: false
        });

        const script = document.createElement('script');
        script.src = 'https://static.24metrics.com/js/index.js';
        script.id = 'adsec'
        this.scriptFile = document.body.appendChild(script);

        await document.addEventListener("adSecurityJSIntegrationEvent", function (e) {
          console.log(e.detail)
          // Place your logic to operate with new data
          ref.vId = e.detail.click_data.fingerprint;
          console.log(ref.vId)
          if (ref.vId !== undefined) {
            router.push({
                  name: 'about',
                  replace: true
                }
            )
          }
        })
      },
    },
    unmounted() {
      console.log("Destroying page")
      const scriptElement = document.getElementById('adsec');
      if (scriptElement) {
        if(document.body.contains(this.scriptFile)) {
          console.log("destroy script")
          while (scriptElement.firstChild) {
            scriptElement.removeChild(scriptElement.firstChild);
          }

        }
      }
    }
  }
</script>