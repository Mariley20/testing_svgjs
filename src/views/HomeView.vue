<template>
<v-container>
<v-row>
  <v-col cols="2">
<!--  -->
  </v-col>
  <v-col cols="3">
    <TextEditor />
  </v-col>
  <v-col cols="7">
  <div>
    <Brand07 />
  </div>

  </v-col>
</v-row>
</v-container>
</template>

<script>
import Brand07 from '@/components/Brand07.vue'
import TextEditor from '@/components/TextEditor.vue'

export default {
  components: {
    Brand07, TextEditor
  }
}
</script>

<style lang="scss" scoped>
</style>
