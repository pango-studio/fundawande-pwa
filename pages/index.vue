<template>
  <div>
    <Navbar></Navbar>
    <div class="wrapper courses-wrapper background-secondary" id="page-wrapper">
      <HeaderBand v-bind:title="coursepage.title.rendered"></HeaderBand>
      <div class="container">
        <div class="row my-md-5">
          <div class="col-12 col-lg-4 mt-3" v-for="course in courses" v-bind:key="course.id">
            <CourseCard v-bind:course="course"></CourseCard>
          </div>
        </div>
      </div>
    </div>
    <Footer></Footer>
  </div>
</template>

<script>
import HeaderBand from '../components/HeaderBand'
import CourseCard from '../components/CourseCard'
import Navbar from '../components/Navbar'
import Footer from '../components/Footer'

import axios from 'axios'

export default {
  components: {
    Navbar,
    HeaderBand,
    CourseCard,
    Footer
  },
  async asyncData({ params }) {
    const courses = await axios.get(
      `http://fundawande:7888/wp-json/wp/v2/courses`
    )
    const coursepage = await axios.get(
      `http://fundawande:7888/wp-json/wp/v2/pages/5072`
    )
    return { courses: courses.data, coursepage: coursepage.data }
  },
  head() {
    return {
      title: this.coursepage.title.rendered
    }
  }
}
</script>

<style lang="scss" scoped>
</style>

