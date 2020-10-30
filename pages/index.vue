<template>
  <div class="container">
    <header-nav-vue @selectedAPage="goToSelectedPage" />
    <div class="all-pages">
      <Home id="Home" class="page active" @click.native="selectPage" />
      <AboutMe id="AboutMe" class="page inactive next" @selectedAPage="goToSelectedPage" @click.native="selectPage" />
      <Projects id="Projects" class="page inactive next2" @click.native="selectPage" />
      <ContactMe id="ContactMe" class="page inactive next2" @click.native="selectPage" />
    </div>
  </div>
</template>

<script>
/* eslint-disable no-console */
import Home from '../components/Home.vue'
import AboutMe from '../components/AboutMe.vue'
import Projects from '../components/Projects.vue'
import HeaderNavVue from '../components/Header-Nav.vue'
import ContactMe from '../components/ContactMe.vue'
export default {
  components: {
    Home,
    AboutMe,
    Projects,
    ContactMe,
    // eslint-disable-next-line vue/no-unused-components
    HeaderNavVue
  },
  mounted () {
    // document.querySelector('.page:nth-of-type(1)').classList.add('active')
  },
  methods: {
    selectPage (e) {
      let pageToShow
      if (e.target.closest('a[data-toggle="nav"]')) {
        pageToShow = document.querySelector(e.target.closest('a[data-toggle="nav"]').getAttribute('href'))
      } else {
        pageToShow = e.target.closest('section')
      }
      this.showPage(pageToShow)
    },
    goToSelectedPage (page) {
      this.showPage(page)
    },
    showPage (pageToShow) {
      const allPages = Array.from(document.querySelectorAll('.page'))
      const pageToShowIndex = allPages.findIndex(page => page === pageToShow)
      let reshuffledPages = []

      if ((allPages.length - 1) - pageToShowIndex >= 1) {
        const siblings = [...allPages].splice(pageToShowIndex + 1, 1)
        reshuffledPages = siblings
      }
      if ((allPages.length - 1) - pageToShowIndex >= 2) {
        const siblings = [...allPages].splice(pageToShowIndex + 1, 2)
        reshuffledPages = siblings
      }

      allPages.forEach((page) => {
        if (!reshuffledPages.includes(page) && page !== pageToShow) {
          reshuffledPages.push(page)
        }
      })

      pageToShow.classList.remove('inactive')
      pageToShow.classList.remove('waiting')
      pageToShow.classList.remove('next')
      pageToShow.classList.add('active')

      reshuffledPages.forEach((page, index) => {
        page.classList.remove('next')
        page.classList.remove('next2')
        if (index === 0) {
          page.classList.add('next')
        } if (index === 1) {
          page.classList.add('next2')
        }
        page.classList.remove('waiting')
        page.classList.remove('active')
        page.classList.add('inactive')
        document.querySelector('nav').classList.remove('open')
        document.querySelector('.menu-toggle').classList.remove('open')
      })
    }
  }
}
</script>

<style lang="scss">
.container {
  margin: 0 auto;
  height: 100vh;
  overflow: hidden;
  width: 100vw;
}

.all-pages {
  z-index: 200;
  perspective: 1200px;
  perspective-origin: 50% -50%;
}

.page.active {
  position: relative;
  transform: translate3d(0px, 0, 0);
  z-index: 5;
}

.page.active.waiting {
  transform: translate3d(0px, 75%, -200px);
   opacity: 0.9;
}

/* .page.waiting {
  z-index: 4 !important;
  position: relative !important;
} */

.page.inactive {
  z-index: 1;
  position: absolute;
  transform: translate3d(0px, 75%, -300px);
}

.page.inactive.next {
  z-index: 4;
   transform: translate3d(0px, 75%, -250px);
   opacity: 0.9;
}

.page.inactive.next2 {
  z-index: 3;
   transform: translate3d(0px, 75%, -300px);
   opacity: 0.9;
}

.page {
  transform: translate3d(0px, 75%, -200px);
  transition: transform 0.45s, opacity 0.45s;
  top: 0;
  box-shadow: 0 -1px 10px rgba(0, 0, 0, 0.1);
}
</style>
