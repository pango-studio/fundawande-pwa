<template>
  <div class="card course-card px-md-3 py-3 mx-md-3 my-3">
    <div class="card-body d-flex flex-column">
      <div class="course-card-header flex-grow-1">
        <h5 class="course-card-title text-bold">{{course.acf.course_title}}</h5>
        <p>0% completed</p>
        <hr>
      </div>
      <div class="course-card-body flex-grow-1">
        <span v-html="course.acf.course_description"></span>
      </div>
      <div class="course-card-footer text-center pt-3 pt-md-5 flex-shrink-1">
        <a class="btn btn-lg primary-btn-fill mx-auto" :href="`/modules/${course.id}`">Start Course</a>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CourseCard',
  props: {
    course: Object
  }
}
</script>

<style lang="scss" scoped>
@import 'assets/theme/utilities.scss';
@import 'assets/theme/variables.scss';

.course-card {
  &-title {
    @include breakpoint(desktop) {
      min-height: 75px;
    }
  }
  @include breakpoint(desktop) {
    min-height: 460px;
  }
}
</style>


