<template>
  <section class="contact">
    <div class="image">
      <div class="text">
        CONTACT ME
      </div>
    </div>
    <div class="content custom-scrollbar">
      <Title main-text="Contact Me" top-text="Contact Info" />

      <form
        validate
        name="contact"
        method="post"
        netlify-honeypot="bot-field"
        data-netlify="true"
        @submit.prevent="handleSubmit"
      >
        <p>SEND ME A MESSAGE</p>
        <label>
          Name:
          <input v-model="form.name" type="text" required placeholder="e.g John Doe">
        </label>
        <label>
          Email:
          <input v-model="form.email" type="email" required placeholder="e.g janedoe@example.com">
        </label>
        <label class="big">
          Message:
          <textarea v-model="form.message" required placeholder="WRITE YOUR MESSAGE HERE">Hello</textarea>
        </label>

        <input type="submit" value="SEND MESSAGE">
      </form>
    </div>
  </section>
</template>

<script>
/* eslint-disable no-console */
export default {
  data () {
    return {
      form: {
        name: '',
        email: '',
        message: ''
      }
    }
  },
  methods: {
    encode (data) {
      return Object.keys(data)
        .map(key => `${encodeURIComponent(key)}=${encodeURIComponent(data[key])}`)
        .join('&')
    },
    handleSubmit () {
      fetch('/', {
        method: 'post',
        headers: {
          'Content-Type': 'application/x-www-urlencoded'
        },
        body: this.encode({
          'form-name': 'contact',
          ...this.form
        }
        )
      })
        .then(() => console.log('sent'))
        .catch(() => console.log('failed'))
    }
  }
}
</script>

<style lang="scss" scoped>
section.contact {
  background: #fff;

  .image {
    background-image: url("/phone3.jpg");
    // background-size: contain;
    background-blend-mode: multiply;
  }

  form {
    margin-top: 30px;
    padding: 2rem;
    width: 100%;
    max-width: 700px;
    border: 1px solid #ccc;
    display: flex;
    justify-content: space-between;
    flex-wrap: wrap;

    p {
      width: 100%;
    }
  }

  form label {
    width: 48%;
    display: inline-block;
    margin: 10px 0;

    &.big {
      width: 100%;
    }

    input {
      width: 100%;
      height: 35px;
      outline: 0;
      border: 1px solid #ccc;
      padding: 2px 10px;

      &:focus {
        border-bottom: 3px solid #2e5090;
      }
    }

    textarea {
      resize: none;
      width: 100%;
      height: 200px;
      @extend input;
      padding: 1rem;
    }
  }

  input[type="submit"] {
    outline: none;
    border: 0;
    height: 40px;
    background: #2e5090;
    color: #fff;
    text-transform: uppercase;
    padding: 10px 30px;
    cursor: pointer;
    border-radius: 4px;
    box-shadow: 0px 0px 10px -4px #333;

    &:hover {
      transform: scale(0.97);
      background: darken($color: #2e5090, $amount: 20%);
    }
  }
}

@media (max-width: 420px) {
  section.contact {
    form {
      label {
        width: 100%;
      }
    }
  }
}
</style>
