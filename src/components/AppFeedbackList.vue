<template>
  <div class="list.item">
    <div>
      <p><strong>{{ comment.email }}</strong></p>
      <small>{{ comment.body }}</small>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    comment: Object
  }
}
</script>

<style>

</style>