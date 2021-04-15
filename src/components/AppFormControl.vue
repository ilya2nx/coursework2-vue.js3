<template>
  <form class="card card-w30">
    <div class="form-control">
      <label for="type">Тип блока</label>
      <select id="type" v-model="blockType">
        <option value="title">Заголовок</option>
        <option value="subtitle">Подзаголовок</option>
        <option value="avatar">Аватар</option>
        <option value="text">Текст</option>
      </select>

    <div class="form-control">
      <label for="value">Значение</label>
      <textarea id="value" rows="3" v-model="blockValue"></textarea>
    </div>

    <button class="btn primary" :disabled='canAdd' @click="addBlock">Добавить</button>

    </div>
  </form>
</template>

<script>
export default {
  emits: ['addBlock'],
  computed: {
    canAdd() {
      return this.blockValue.length < 3
    }
  },
  data() {
    return {
      blockType: 'title',
      blockValue: ''
    }
  },
  methods: {
    addBlock() {
      this.$emit('addBlock', this.blockValue, this.blockType)
      this.blockValue = ''
      this.blockType = 'title'
    }
  }
}
</script>

<style>

</style>