<template>
  <div class="wrapper single-course-wrapper background-secondary" id="page-wrapper">
    <HeaderBand v-bind:title="course.acf.course_title"></HeaderBand>
    <div class="container">
      <div class="row my-md-5">
        <div class="col-12 mt-3" v-for="module in modules" v-bind:key="module.id">
          <ModuleCard v-bind:module="module" v-bind:course="course"></ModuleCard>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import HeaderBand from '../../components/HeaderBand'
import ModuleCard from '../../components/ModuleCard'

import axios from 'axios'

export default {
  name: 'SingleCoursePage',
  components: {
    HeaderBand,
    ModuleCard
  },
  async asyncData({ params }) {
    const course = await axios.get(
      `http://fundawande:7888/wp-json/wp/v2/courses/${params.id}`
    )
    const modules = await axios.get(
      `http://fundawande:7888/wp-json/lms/v1/modules/${params.id}`
    )
    return { course: course.data, modules: modules.data }
  },
  head() {
    return {
      title: this.course.acf.course_title
    }
  }
}
</script>

<style lang="scss" scoped>
</style>

