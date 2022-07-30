<template>
  <div class="card card-w70">
    <template v-if="blocks.length">
      <component
        v-for="block in blocks"
        :key="block.id"
        :is="'resume-' + block.type"
        v-bind="{value: block.value}"
      ></component>
    </template>
    <h3 v-else>Добавьте первый блок, чтобы увидеть результат</h3>
  </div>
</template>

<script>
import ResumeAvatar from './resumeParts/ResumeAvatar.vue'
import ResumeSubtitle from './resumeParts/ResumeSubtitle.vue'
import ResumeText from './resumeParts/ResumeText.vue'
import ResumeTitle from './resumeParts/ResumeTitle.vue'

export default {
  props: ['blocks'],
  components: {
    ResumeTitle,
    ResumeText,
    ResumeSubtitle,
    ResumeAvatar
  }
}
</script>