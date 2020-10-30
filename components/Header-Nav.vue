<template>
  <div class="header-nav-wrapper">
    <header>
      <div class="logo">
        ABEYDEV
      </div>
      <div ref="menu-btn" class="menu-toggle" @click="toggleMenu">
        <button>
          <span>Menu</span>
        </button>
      </div>
    </header>

    <nav ref="nav">
      <ul>
        <li>
          <a href="#Home" @click.prevent="selectPageById">Home</a>
        </li>
        <li>
          <a href="#AboutMe" @click.prevent="selectPageById">About Me</a>
        </li>
        <li>
          <a href="#Projects" @click.prevent="selectPageById">Projects</a>
        </li>
        <li>
          <a href="#ContactMe" @click.prevent="selectPageById">Contact Me</a>
        </li>
      </ul>
    </nav>
  </div>
</template>

<script>
/* eslint-disable semi */
/* eslint-disable quotes */
/* eslint-disable no-console */
/* eslint-disable space-before-function-paren */
export default {
  methods: {
    toggleMenu() {
      const menuBtn = this.$refs["menu-btn"];
      menuBtn.classList.toggle("open");
      document.querySelectorAll('.page').forEach((page) => {
        if (page.classList.contains('active')) {
          page.classList.toggle('waiting')
        }
      })
      this.$refs.nav.classList.toggle('open')
    },
    selectPageById(e) {
      const pageId = e.target.getAttribute("href");
      const page = document.querySelector(pageId);
      this.$emit("selectedAPage", page);
      this.$refs.nav.classList.remove('open')
    }
  }
};
</script>

<style lang="scss" scoped>

.header-nav-wrapper {
position: absolute;
width: 100%;
    z-index: 400;
  header {
      position: fixed;
      right: 0;
    display: flex;
    background: #2e5090;
    color: #fff;
    width: fit-content;
    font-weight: 700;
    font-size: 30px;
    height: 60px;



    .logo {
      width: 240px;
      display: flex;
      justify-content: flex-start;
      align-items: center;
      padding: 0px 12px;
    }

    .menu-toggle {
      button {
        outline: none;
        border: none;
        background: #000;
        height: 100%;
        width: 60px;
        position: relative;
        &::before,
        &::after {
          transition: all 250ms ease-in-out;
          content: "";
          position: absolute;
          height: 2px;
          display: block;
          left: 12px;
          right: 12px;
          background-color: #fff;
        }
        &::after {
          bottom: 15px;
        }

        &::before {
          top: 15px;
        }

        span {
          transition: all 250ms ease-in-out;
          top: 50%;
          background: #fff;
          display: block;
          height: 2px;
          left: 5px;
          right: 5px;
          position: absolute;
          transform: translateY(-50%);
          color: transparent;
        }
      }

      &.open {
        button {
          &::after {
            bottom: 50%;
            transform: rotate3d(0, 0, 1, 45deg) translateY(50%);
          }
          &::before {
            top: 50%;
            transform: rotate3d(0, 0, 1, -45deg) translateY(-50%);
          }

          span {
            opacity: 0;
            transform: scale(0);
          }
        }
      }
    }
  }

  nav {
      z-index: 300;
        height: 10vh;
    padding: 1rem;
    pointer-events: none;
    // transform: translate3d(0, 150px, 0);
    transition: all 500ms ease-in-out;
    opacity: 0;
    &.open {
        height: 50vh;
    //    transform: translate3d(0, 0, 0);
        pointer-events: all;
        opacity: 1;
    }

    ul {
      width: 100%;
      height: 100%;
      display: flex;
      align-items: center;
      justify-content: center;
      list-style: none;

      li {
        margin: 0px 10px;
        text-transform: uppercase;

        a {
          text-decoration: none;
          color: #fff;
        }
      }
    }
  }
}

@media (max-width: 700px) {
    .header-nav-wrapper header {
      width: 100%;
      justify-content: space-between;
    }
}

@media (max-width: 600px) {
  .header-nav-wrapper {
    nav {
      transition: opacity 300ms;
      &.open {
          li {
            opacity: 1;
          }
      }


      ul {
        flex-wrap: wrap;
        align-content: center;
        li {
          margin: 5px 0;
          width: 100%;
          display: flex;
          justify-content: center;
          opacity: 0;
        }
      }
    }
  }
}
</style>
