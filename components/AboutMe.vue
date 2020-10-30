<template>
  <section class="about">
    <div class="image">
      <div class="text">
        ABOUT ME
      </div>
    </div>

    <div class="content custom-scrollbar">
      <Title top-text="who i am" main-text="about me" />

      <div class="about__me">
        <div class="my-pic">
          <img src="/me1.png" alt="my picture">
        </div>
        <div class="text">
          <p>
            I am a self-taught (M.E.V.N) stack developer who uses modern
            technologies like VueJs, Node.js, Express, MongoDB, GraphQL,
            WebSockets etc to translate designs and mockups into functional,
            quality and responsive websites/webapps.
          </p>

          <p>
            I wrote my first "Hello World" in March 2018, Since then, I've
            participated in the #ALCwithGoogle in 2018 and got a
            <a
              href="https://res.cloudinary.com/abeydev/image/upload/v1596831102/portfolio/doc/nanodeg_pfjfph.pdf"
            >
              Nanodegree</a>
            @ Udacity that same year November.
          </p>

          <p>
            I've picked up quite a few stuff since then on my own: Vuejs,
            NodeJs, ExpressJs, WebSockets, GraphQL etc...
          </p>

          <p>
            When I'm not doing anything related to coding 👨‍💻, I watch anime 🤡,
            and sometimes biking 🚴‍♂️.
          </p>

          <p>
            If you are looking for a web developer to help bring your ideas to
            life, work on an existing project, or join a team of developers? I
            am currently available to take on any project.
          </p>

          <div class="actions">
            <a
              href="https://res.cloudinary.com/abeydev/image/upload/v1596831103/portfolio/doc/Abiodun-Emmanuel-CV_whd3ba.pdf"
            >Download Resumé 📋</a>

            <a href="mailto:abiodunolunu@gmail.com">Contact Me 📞</a>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
/* eslint-disable no-console */
import Title from './UI Components/Title.vue'
export default {
  components: {
    Title
  },
  methods: {
    goToA (e) {
      const pageId = e.target.getAttribute('href')
      const page = document.querySelector(pageId)
      this.$emit('selectedAPage', page)
    }
  }
}
</script>

<style lang="scss" scoped>
section.about {
  width: 100%;
  height: 100vh;
  background: #fff;

  div.content {
    padding-top: 80px;
    overflow-y: auto;
    .about__me {
      margin-top: 40px;
      display: flex;
      justify-content: flex-start;
      flex-wrap: wrap;
      > div {
        margin: 1em;
      }
    }

    .my-pic {
      max-width: 30px;
      min-width: 240px;
      height: auto;
      max-height: 300px;
      position: relative;
      z-index: 1;

      &::after {
        display: none;
        content: "";
        position: absolute;
        background: transparentize(#2e5090, $amount: 0.5);
        top: -20px;
        left: -20px;
        height: 100%;
        width: 100%;
        z-index: -1;
      }
      img {
        width: 100%;
        height: 100%;
        object-fit: cover;
      }
    }

    .text {
      max-width: 500px;

      p {
        margin: 12px 0;
        color: #002;

        a {
          color: #2e5090;
          text-decoration: underline;
          transition: font-weight 250ms ease-in-out;

          &:hover {
            font-weight: 600;
          }
        }
      }
    }

    .actions {
      width: 100%;
      display: flex;
      flex-wrap: wrap;
      justify-content: space-between;
      gap: 10px;
      a {
        margin: 0px 5px;
        display: inline-flex;
        justify-content: center;
        align-items: center;
        height: 40px;
        background: #2e5090;
        color: #fff;
        text-transform: uppercase;
        font-size: 14px;
        padding: 0px 20px;
        border-radius: 8px 0 8px 0;
        cursor: pointer;
        transition: all 500ms ease-in-out;
        box-shadow: -10px 0px 20px -10px #333;
        &:hover {
          box-shadow: 10px 0px 20px -10px #333;
          background: darken(#2e5090, 20%);
          border-radius: 0 8px 0 8px;
          transform: scale(0.97);
        }
      }
    }
  }
}

@media (max-width: 700px) {
  section.about {

    div.content {
      .about__me {

      }

      .text {
        max-width: 100%;
      }

      .actions {
      }
    }
  }
}
</style>
