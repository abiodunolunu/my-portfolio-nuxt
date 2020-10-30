<template>
  <section class="projects">
    <div class="image">
      <div class="text">
        PROJECTS
      </div>
    </div>

    <div class="content custom-scrollbar">
      <Title main-text="Personal Projects" top-text="Projects" />

      <div class="projects">
        <div
          v-for="(project, index) in projects"
          :key="index"
          class="project__showcase"
        >
          <div class="project__image-link">
            <img :src="project.imageLink" :alt="project.title + ' picture'">
            <div class="project__links">
              <a :href="project.links.code" target="_blank">
                CODE <i class="fab fa-github" />
              </a>
              <a
                :href="project.links.live"
                target="_blank"
              >LIVE <i
                class="fas fa-globe"
              /></a>
            </div>
          </div>
          <div class="project__title">
            <h3>{{ project.title }}</h3>
          </div>
          <div class="project__stack">
            <ul>
              <li v-for="(s, index) in project.stack" :key="index">
                {{ s }}
              </li>
            </ul>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  data () {
    return {
      projects: [
        {
          title: 'Asknonymous',
          desc:
            'A website where users can send and receive anonymous messages with shareable links.',
          stack: ['HTML', 'CSS', 'EXPRESS', 'MONGODB'],
          imageLink:
            'https://res.cloudinary.com/abeydev/image/upload/v1596743782/portfolio/Asknoymous_nk09jb.png',
          links: {
            live: 'https://asknonymos.herokuapp.com/',
            code: 'https://github.com/abiodunolunu/Asknonymous'
          }
        },
        {
          title: 'My Picture App (MINI IG 😂)',
          desc: 'A website where users can share and interact with pictures.',
          stack: ['HTML', 'CSS', 'SCSS', 'Vue.Js', 'Express', 'GraphQL'],
          imageLink:
            'https://res.cloudinary.com/abeydev/image/upload/v1596743781/portfolio/picture-app_hrjubl.png',
          links: {
            live: 'https://my-picture-app.herokuapp.com/',
            code: 'https://github.com/abiodunolunu/my-picture-app---server'
          }
        },
        {
          title: 'Football live chat',
          desc: 'real time live chat app/website for football/soccer fans.',
          stack: ['HTML', 'CSS', 'JS', 'EXPRESS', 'MONGODB', 'WEBSOCKETS'],
          imageLink:
            'https://res.cloudinary.com/abeydev/image/upload/v1596743782/portfolio/SoccerChat_rg63xz.png',
          links: {
            live: 'https://football-live-chat.herokuapp.com/',
            code:
              'https://github.com/abiodunolunu/football-soccer-chat-LIVE-chat-app-with-rooms'
          }
        },
        {
          title: 'URL Shortner',
          desc:
            'A website where you can convert long links into really short ones',
          stack: ['HTML', 'CSS', 'SCSS', 'EXPRESS', 'MONGODB'],
          imageLink:
            'https://res.cloudinary.com/abeydev/image/upload/v1596857262/portfolio/url-shortner_kfprkb.png',
          links: {
            live: 'https://abedev.herokuapp.com/',
            code: 'https://github.com/abiodunolunu/url-shortner'
          }
        }
      ]
    }
  }
}
</script>

<style lang="scss" scoped>
section {
  width: 100%;
  height: 100vh;
  background: #fff;

  div.image {
    background-image: url("/project.png");
    background-color: #2e5090;
  }

  &.waiting,
  &.inactive {
    .content {
      overflow: hidden;
    }
  }

  .content {
    overflow-y: auto;
  }
  .projects {
    margin-top: 40px;
    display: flex;
    flex-wrap: wrap;
    justify-content: flex-start;
    max-width: 1000px;
  }

  .project__showcase {
    margin: 20px;
    height: 380px;
    border: 1px solid #ddd;
    border-bottom: 4px solid #2e5090;
    padding: 1rem;
    display: inline-block;
    vertical-align: top;
    flex-basis: 50%;
    max-width: 350px;
    min-width: 350px;
    .project__image-link {
      position: relative;
      width: 100%;
      height: 240px;
      img {
        width: 100%;
        height: 100%;
        object-fit: cover;
        object-position: center;
      }
    }

    &:hover {
      .project__links {
        transform: scale(1);
      }
    }

    .project__links {
      transform: scale(0);
      transform-origin: bottom;
      transition: transform 300ms ease-out;
      position: absolute;
      background: rgba($color: #000000, $alpha: 0.5);
      left: 0;
      height: 60px;
      bottom: 0;
      color: #fff;
      width: 100%;
      display: flex;
      justify-content: space-between;
      align-items: center;

      a {
        display: inline-flex;
        justify-content: center;
        align-items: center;
        padding: 0px 12px;
        width: 100px;
        margin: 2px 5px;
        background: #2e5090;
        height: 32px;
        font-size: 14px;
        border-radius: 5px 0 5px 0;
        i {
          margin-left: 5px;
        }

        &:hover {
          background: lighten(#2e5090, $amount: 10%);
        }
      }
    }

    .project__title {
      margin-top: 5px;
      width: 100%;
      h3 {
        font-weight: 600;
        font-size: 18px;
        color: #151515;
      }
    }

    .project__stack {
      ul {
        margin-top: 10px;
        list-style: none;
        max-width: 280px;
        li {
          font-size: 10px;
          display: inline-block;
          margin: 0 5px;
          padding: 0px 10px;
          color: #fff;
          position: relative;
          z-index: 1;
          &::after {
            content: "";
            position: absolute;
            top: 0;
            left: 0;
            height: 100%;
            width: 100%;
            background: #2e5090;
            z-index: -1;
            transform: skew(-20deg);
            transition: transform 200ms ease-in-out;
          }

          &:hover {
            &::after {
              transform: skew(20deg);
            }
          }
        }
      }
    }
  }
}

@media (max-width: 700px) {
  section {
    .projects {
      justify-content: center;
      padding: 10px;
    }

    .project__showcase {
     width: 100%;
     flex-basis: 80%;
     max-width: 100%;
      // min-width: 300px;
    }
  }
}
</style>
