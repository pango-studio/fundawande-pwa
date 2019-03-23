<template>
  <div>
    <Navbar></Navbar>
    <div>
      <HeaderBand></HeaderBand>
    </div>
    <Footer></Footer>
  </div>
</template>

<script>
import HeaderBand from '../../components/HeaderBand'
// import UnitCard from '../../components/UnitCard'
import Navbar from '../../components/Navbar'
import Footer from '../../components/Footer'

import axios from 'axios'

export default {
  name: 'SingleModulePage',
  components: {
    Navbar,
    HeaderBand,
    // UnitCard,
    Footer
  },
  async asyncData({ params }) {
    const units = await axios.get(
      'http://fundawande:7888/wp-json/lms/v1/units/'
    )
    const module = await axios.get(
      `http://fundawande:7888/wp-json/lms/v1/modules/1421`
    )
    return {
      units: units.data,
      module: module.data
      // modules: modules.data
    }
  },
  created() {
    var _id = this.$route.params.id
    var regex = /(course_id=[0-9]{2,4})&(module_id=[0-9]{2,4})/
    var contents = _id.match(regex)

    this.course_id = contents[1]
    this.module_id = contents[2]
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

