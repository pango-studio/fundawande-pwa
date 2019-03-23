<template>
  <div id="module-card" class="my-3 d-inline-block w-100">
    <a class="module-link" :href="`/units/course_id=${course.id}&module_id=${module.term_id}`">
      <div class="card">
        <div class="card-body">
          <div class="row">
            <!-- Module Info -->
            <div class="col-12 col-md-10">
              <div class="header d-flex">
                <div :class="moduleBG" class="header-counter mr-2 p-4">
                  <h4 class="m-0">{{module.module_number}}</h4>
                </div>
                <div class="header-text">
                  <h4>{{module.module_title}}</h4>
                  <h5
                    :class="moduleText"
                    class="module-progress d-none d-sm-block"
                  >0/{{module.units.length}} Units Completed</h5>
                </div>
              </div>
              <hr>
              <p>{{module.module_description}}</p>
            </div>
            <!-- Module Navigation Button -->
            <div class="col-12 col-md-2 module-nav d-flex">
              <h4 :class="moduleText" class="module-progress m-3 d-sm-none">0/0 Units Completed</h4>
              <div :class="moduleBG" class="module-nav-button p-3 d-flex">
                <img
                  width="100px"
                  class="img img-responsive d-none d-md-block p-3"
                  src="~/assets/svg/arrow_right.svg"
                >
                <h5 class="text-center my-0">
                  Go to Module
                  <img class="p-2 d-md-none" src="~/assets/svg/arrow_right.svg">
                </h5>
              </div>
            </div>
          </div>
        </div>
      </div>
    </a>
  </div>
</template>

<script>
export default {
  name: 'Module',
  props: {
    course: Object,
    module: Object
  },
  computed: {
    moduleBG() {
      return `module-bg-${this.module.module_number}`
    },
    moduleText() {
      return `module-text-${this.module.module_number}`
    }
  }
}
</script>

<style lang="scss" scoped>
@import 'assets/theme/utilities.scss';
@import 'assets/theme/variables.scss';

.module-link {
  color: $text-primary__colour;
  &:hover {
    cursor: pointer;
    text-decoration: none;
    color: $text-primary__colour;
  }
}

.card {
  &.current {
    border: 3px solid $brand-primary__colour;
    margin-top: 3rem !important;
    .current-module-text {
      display: block;
      position: absolute;
      font-style: italic;
      color: white;
      padding: 6px 18px;
      background: $brand-primary__colour;
      border-radius: 5px 5px 0 0;
      left: 2rem;
      @include breakpoint(tablet) {
        top: -40px;
      }
      @include breakpoint(phone) {
        top: -30px;
      }
    }
  }
  &:hover {
    -webkit-box-shadow: 0px 0px 10px 0px rgba(0, 0, 0, 0.3);
    box-shadow: 0px 0px 10px 0px rgba(0, 0, 0, 0.3);
  }
  .header {
    align-items: center;
    &-counter {
      border-radius: 5px;
      h2,
      h3,
      h4,
      h5 {
        color: $white;
      }
    }
  }
  .module {
    &-nav {
      align-items: center;
      justify-content: center;
      &-button {
        border-radius: 5px;
        height: 100%;
        flex-direction: column;
        justify-content: center;
        h2,
        h3,
        h4,
        h5 {
          color: $white;
        }
      }
    }
  }
}
</style>


