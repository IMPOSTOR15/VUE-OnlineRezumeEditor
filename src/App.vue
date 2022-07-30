<template>
  <div class="container column">
    <app-resume-form @block-added="addBlock"></app-resume-form>
    <app-rezume :blocks="blocks"></app-rezume>
  </div>
  <app-loader v-if="loading"></app-loader>\
  <app-coments
    :coments="coments"
    @load="loadComents"
  ></app-coments>
</template>

<script>
import AppResumeForm from './components/AppResumeForm.vue'
import AppRezume from './components/AppRezume.vue'
import AppLoader from './components/AppLoader.vue'
import AppComents from './components/AppComments.vue'
import axios from 'axios'

export default {
  data() {
    return {
      text: '',
      value: 'title',
      loading: false,
      coments: [],
      blocks: [],

    }
  },
  methods: {
    async loadComents() {
      this.loading = true
      const {data} = await axios.get('https://jsonplaceholder.typicode.com/comments?_limit=42')
      this.coments = Object.keys(data).map(key => {
          return {
            id: key,
            ...data[key]
        }
      })
      console.log(this.coments)
      this.loading = false
    },
    addBlock(block) {
      this.blocks.push(block)
    }
  },

  components: {
    AppRezume,
    AppLoader,
    AppComents,
    AppResumeForm,
  }
}
</script>

<style>
  .avatar {
    display: flex;
    justify-content: center;
  }

  .avatar img {
    width: 150px;
    height: auto;
    border-radius: 50%;
  }
</style>
