<template>
    <div id="wrapper">
        <main>
            <b>Welcome!</b>

            <ul>
                <li v-for="file in files">{{file}}</li>
            </ul>
        </main>
    </div>
</template>

<script>
  import fs from 'fs'

  export default {
    name: 'landing-page',
    data () {
      return {
        'files': []
      }
    },
    created () {
      fs.readFile('/tmp/open-with', 'utf8', (err, data) => {
        if (err) {
          throw err
        }

        const files = JSON.parse(data)

        if (files.length === 0) {
          return
        }

        this.files = files
      })
    },
    methods: {}
  }
</script>

<style lang="scss">
    #wrapper {
        text-align: center;
        font-family: Arial, "Helvetica Neue", Helvetica, sans-serif
    }
</style>
