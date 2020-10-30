<template>
  <section class="home">
    <div class="image">
      <img src="/me3.png" alt="">
    </div>
    <div class="content custom-scrollbar">
      <div class="text">
        <p>Hi, There</p>
        <h1>I'm Olunu Abiodun</h1>
        <p>Front-End Developer</p>
        <a href="https://res.cloudinary.com/abeydev/image/upload/v1596831103/portfolio/doc/Abiodun-Emmanuel-CV_whd3ba.pdf">DOWNLOAD RÉSUME</a>
      </div>
      <div class="socials">
        <ul>
          <li>
            <a href="https://twitter.com/findbyusername"><i class="fab fa-twitter" /></a>
          </li>
          <li>
            <a href="https://linkedin.com/in/abiodunolunu"><i class="fab fa-linkedin" /></a>
          </li>
          <li>
            <a href="https://github.com/abiodunolunu"><i class="fab fa-github" /></a>
          </li>
          <li>
            <a href="mailto:abiodunolunu@gmail.com"><i class="fa fa-envelope" /></a>
          </li>
        </ul>
      </div>
    </div>
  </section>
</template>

<style lang="scss" scoped>
section.home {
  width: 100%;
  height: 100vh;
  background: #fff;

  div.image {
    background: #2e5090;
    height: 100%;
    display: flex;
    align-items: flex-end;
    padding: 0;
    img {
      filter: drop-shadow(0px 0px 5px #061838);
      width: 100%;
      // height: 100%;
      object-fit: contain;
    }
  }

  div.content {
    display: flex;
    align-items: center;
align-content: center;
max-height: 100vh;
    .text {
      p {
        text-transform: uppercase;
        font-size: 18px;
        color: #292929;
      }

      h1 {
        text-transform: uppercase;
        font-size: 60px;
        color: #292929;
        line-height: 1;
      }
      a {
        margin-top: 20px;
        background: #2e5090;
        text-decoration: none;
        color: #fff;
        display: inline-flex;
        justify-content: center;
        align-items: center;
        height: 42px;
        font-size: 15px;
        padding: 12px 22px;
        border-radius: 5px;
        border: none;
        box-shadow: 0px 8px 15px rgba(0, 0, 0, 0.1);

        &:hover {
          background-color: darken(#2e5090, $amount: 20%);
        }
      }
    }
  }

  .socials {
    position: absolute;
    bottom: 20px;
    right: 20px;
    ul {
      display: flex;
      li {
        margin: 0px 5px;
        list-style: none;

        a {
          i {
            font-size: 30px;
            color: #2e5090;
            &:hover {
              &.fa-twitter {
                color: #00acee;
              }
              &.fa-linkedin {
                color: #0e76a8;
              }
              &.fa-github {
                color: #333;
              }
            }
          }
        }
      }
    }
  }
}

@media (max-width: 700px) {
  section.home {
   div.image {
     display: none;
   }

   div.content {
     .text {
       margin: auto;
       text-align: center;
       h1 {
         font-size: 50px;
       }
     }
   }
  }
}
</style>
