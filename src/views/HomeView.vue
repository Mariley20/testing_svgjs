<template>
<v-container fluid>
<v-row>
  <v-col cols="2">
<!--  -->
  </v-col>
  <v-col cols="4">
    <TextEditor />
  </v-col>
  <v-col cols="6">
  <div>
    <Brand7A />
  </div>

  </v-col>
</v-row>
</v-container>
</template>

<script>
import Brand7A from '@/components/Brand7A.vue'
import TextEditor from '@/components/TextEditor.vue'

export default {
  components: {
    Brand7A, TextEditor
  }
}
</script>

<style lang="scss" scoped>
</style>
