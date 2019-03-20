<template>
  <div class="container-fluid background-primary">
    <div class="row course-title">
      <div class="col-12 text-center">
        <h1 class="m-4 text-bold">{{title}}</h1>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HeaderBand',
  props: {
    title: String
  }
}
</script>

<style lang="scss" scoped>
</style>


