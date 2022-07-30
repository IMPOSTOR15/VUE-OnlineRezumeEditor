<template>
  <div class="container">
    <p>
      <button class="btn primary" @click="($emit('load'), showComents = true)">Загрузить комментарии</button>
    </p>
    <div class="card" v-if="showComents === true">
      <h2>Комментарии</h2>
      <ul class="list">
        <li class="list-item" v-for="coment in coments" :key="coment.id">
          <div>
            <p><strong>{{coment.email}}</strong></p>
            <small>{{coment.body}}</small>
          </div>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  emits: ['load'],
  props: ['coments'],
  data() {
    return {
      showComents: false
    }
  }
}
</script>

<style scoped>
  .coment {
    display: flex;
  }
</style>
