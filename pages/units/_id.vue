<template>
  <div>
    <HeaderBand></HeaderBand>
  </div>
</template>

<script>
import HeaderBand from '../../components/HeaderBand'
// import UnitCard from '../../components/UnitCard'

import axios from 'axios'

export default {
  name: 'SingleModulePage',
  components: {
    HeaderBand
    // UnitCard,
  },
  async asyncData({ params }) {
    var _id = params.id
    var regex = /course_id=([0-9]{2,4})&module_id=([0-9]{2,4})/
    var contents = _id.match(regex)
    var course_id = contents[1]
    var module_id = contents[2]

    const units = await axios.get(
      `http://fundawande:7888/wp-json/lms/v1/units/course_id=${course_id}&module_id=${module_id}`
    )
    const module = await axios.get(
      `http://fundawande:7888/wp-json/lms/v1/modules/${course_id}`
    )
    return {
      units: units.data,
      module: module.data
    }
  },
  head() {
    return {
      // title: this.course.acf.course_title
    }
  }
}
</script>

<style lang="scss" scoped>
</style>

