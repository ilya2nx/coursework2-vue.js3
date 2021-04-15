<template>
  <div class="container column">
    <AppFormControl @add-block='addBlock'></AppFormControl>
    <AppBlockContainer>
      <template #title v-if="resume.title">
        <AppBlockTitle :title="resume.title"></AppBlockTitle>
      </template>
      <template #avatar v-if="resume.avatar">
        <AppBlockAvatar :src="resume.avatar"></AppBlockAvatar>
      </template>

      <template #content v-if="resume.content.length !== 0">
        <AppBlockContent v-for="block in resume.content" :key="block.subtitle">
          <template #subtitle v-if="block.subtitle">
            <AppBlockSubtitle :subtitle="block.subtitle"></AppBlockSubtitle>
          </template>
          <template #text v-if="block.text">
            <AppBlockText :text="block.text"></AppBlockText>
          </template>
        </AppBlockContent>
      </template>
    </AppBlockContainer>
  </div>
  <AppFeedbackSection></AppFeedbackSection>
</template>

<script>
import AppFormControl from "@/components/AppFormControl.vue";
import AppBlockContainer from "@/components/AppBlockContainer";
import AppBlockTitle from "@/components/AppBlockTitle";
import AppBlockAvatar from "@/components/AppBlockAvatar";
import AppBlockContent from "@/components/AppBlockContent";
import AppBlockSubtitle from "@/components/AppBlockSubtitle";
import AppBlockText from "@/components/AppBlockText";
import AppFeedbackSection from "@/components/AppFeedbackSection"
export default {
  components: {
    AppFormControl, 
    AppBlockContainer, 
    AppBlockTitle, 
    AppBlockAvatar, 
    AppBlockContent, 
    AppBlockSubtitle, 
    AppBlockText,
    AppFeedbackSection
  },
  data() {
    return {
      resume: {
        title:'',
        avatar: '',
        content: []
      }
    }
  },
  methods: {
    addBlock(value, type) {
      if (type === 'title' || type === 'avatar') {
        this.resume[type] = value
      } else {
        const tempContent = {subtitle: '', text: ''}
        tempContent[type] = value
        this.resume.content.push(tempContent)
      }
    }
  }
}
</script>

<style>

</style>
