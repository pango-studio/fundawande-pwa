<template>
  <div class="footer-wrapper" id="wrapper-footer">
    <footer id="site-footer" class="py-2">
      <div class="container-fluid">
        <div class="row">
          <div class="col-12">
            <div class="container-fluid">
              <div class="row justify-content-md-between justify-content-center">
                <!-- Copyright Info -->
                <div class="col-auto align-self-center">
                  <span class="footer-nav-text">&copy; Funda Wande</span>
                </div>
                <!-- Footer Links -->
                <div
                  class="col-md-auto col-12 align-self-center flex-first flex-md-last mt-3 mt-md-0 text-center"
                >
                  <!-- {% for footer_link in options.footer_links %}
                                <a target="_blank" class="align-self-center d-md-inline-block d-block  pl-md-4 pr-md-0 px-2" href="{{footer_link.link}}">
                                    {% if lang.id == 'eng' %}
                                        {{footer_link.eng_title}}
                                    {% else %}
                                        {{footer_link.xho_title}}
                                    {% endif %}
                                </a>
                  {% endfor %}-->
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </footer>
    <!-- #site-footer -->
  </div>
</template>

<script>
export default {
  name: 'Footer'
}
</script>

<style lang="scss" scoped>
@import 'assets/theme/variables.scss';
@import 'assets/theme/utilities.scss';

#site-footer {
  background-color: #7c7c7c;
  box-shadow: 0 2px 1px 0 $brand-primary__colour;
  color: $white;
  a {
    color: $white;
    text-decoration: none;
    &:hover {
      text-decoration: underline;
    }
  }
}
</style>

