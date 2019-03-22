<template>
  <div id="wrapper-navbar" class="wrapper-fluid wrapper-navbar">
    <nav class="navbar navbar-expand-lg d-flex align-items-center h-100">
      <!-- Main Menu Button -->
      <div id="main-menu-button-container" class="px-4 h-100 d-flex align-items-center">
        <a
          id="main-menu-button"
          class="nav-link"
          href="#"
          role="button"
          data-toggle="modal"
          data-target="#main-menu-modal"
        >
          <!-- Add conditional for showing open or close menu text -->
          <span class="menu-btn-text ml-2 text-uppercase">Open Menu</span>
        </a>
      </div>

      <!-- View Courses Button -->
      <a class="d-none d-lg-block ml-2 pr-4" href="#">
        <!-- {{ source('assets/menu/courses_navbar_icon.svg') }} -->
        <span class="ml-2">View Courses</span>
      </a>
    </nav>
  </div>
</template>

<script>
export default {
  name: 'Navbar'
}
</script>

<style lang="scss" scoped>
@import 'assets/theme/variables.scss';
@import 'assets/theme/utilities.scss';

#wrapper-navbar {
  height: $navbar-height;
  background-color: #4a4a4a;
  box-shadow: 0 2px 1px 0 $brand-primary__colour;
  position: fixed;
  width: 100%;
  z-index: 10000; //Changed to make sure that it displays on top of walkthrough modals.

  .navbar {
    padding: 0;
    #main-menu-button {
      border: 2px solid #ffffff;
      border-radius: 6px;
      padding: 6px;
      height: 44px;
      color: white;
      // Hamburger Nav styling
      .menu-btn-text {
        @include breakpoint(phone) {
          line-height: 15px;
          text-align: center;
          display: block;
          width: 50px;
        }
      }
      .nav-hamburger {
        display: block;
        position: relative;
        overflow: hidden;
        background: transparent;
        margin: 0;
        padding: 0;
        width: $ham-button-width;
        height: $ham-button-height;
        font-size: 0;
        text-indent: -9999px;
        appearance: none;
        box-shadow: none;
        border-radius: 2px;
        border: none;
        cursor: pointer;
        transition: background $ham-button-transistion-duration;
        &:focus {
          outline: none;
        }
        span {
          transition: background 0s $ham-button-transistion-duration;
          display: block;
          position: absolute;
          top: 10px;
          left: $ham-button-pad;
          right: $ham-button-pad;
          height: $ham-bar-thickness;
          background: white;
          border-radius: 3px;
          &::before,
          &::after {
            position: absolute;
            display: block;
            left: 0;
            width: 100%;
            height: $ham-bar-thickness;
            border-radius: 3px;
            background-color: white;
            content: '';
            transition-duration: $ham-button-transistion-duration,
              $ham-button-transistion-duration;
            transition-delay: $ham-button-transistion-duration, 0s;
          }
          &::before {
            top: -$ham-button-bar-space;
            transition-property: top, transform;
          }
          &::after {
            bottom: -$ham-button-bar-space;
            transition-property: bottom, transform;
          }
        }
        & ~ .close-text {
          display: none;
        }
        &.is-active {
          z-index: 1051;
          span {
            background: none;
            &::before,
            &::after {
              transition-delay: 0s, $ham-button-transistion-duration;
            }
            &::before {
              top: 0;
              transform: rotate(45deg);
            }
            &::after {
              bottom: 0;
              transform: rotate(-45deg);
            }
          }
          & ~ .close-text {
            display: block;
          }
          & ~ .open-text {
            display: none;
          }
        }
      }
    }
  }
  &.main-menu-active {
    z-index: 1051;
    box-shadow: none;
    #main-menu-button-container {
      background: white;
      border-radius: 0 6px 0 0;
      #main-menu-button {
        border: 2px solid $text-primary__colour;
        color: $text-primary__colour;
        .nav-hamburger {
          span {
            &:after,
            &:before {
              background: $text-primary__colour;
            }
          }
        }
      }
    }
  }
  a {
    color: white;
    display: flex;
    align-items: center;
    &:hover {
      opacity: 0.8;
      text-decoration: none;
    }
  }

  .change-lang {
    .change-lang-icon {
      background-color: white;
      border-radius: 3px;
      color: #4a4a4a;
      height: 27px;
      width: 31px;
      text-align: center;
      font-size: 8px;
    }
  }
}
</style>

