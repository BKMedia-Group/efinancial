<template>
  <div class="container">
    <div>
      <img src="~/assets/images/logo.svg" alt="" />
      <h1 class="title">
        efinancial
      </h1>
      <h2 class="subtitle">
        Front end for efinancial landing page
      </h2>
      <div class="links">
        <a href="https://nuxtjs.org/" target="_blank" class="button--green">
          Documentation
        </a>
        <a
          href="https://github.com/nuxt/nuxt.js"
          target="_blank"
          class="button--grey"
        >
          GitHub
        </a>
      </div>
      <Modal :visible="isVisible1" @close="isVisible1 = false">
        content
      </Modal>
      <Modal :visible="isVisible2" @close="isVisible2 = false" />
      <button type="button" @click="isVisible1 = true" name="button">
        Show
      </button>
      <button type="button" @click="isVisible2 = true" name="button">
        Show 2
      </button>
      <form
        id="app"
        @submit="checkForm"
        action="https://vuejs.org/"
        method="post"
        novalidate="true"
      >
        <p>
          <label for="name">Name</label>
          <input id="name" v-model="name" type="text" name="name" />
        </p>
        <p>
          <label for="email">Email</label>
          <input id="email" v-model="email" type="email" name="email" />
        </p>
        <p>
          <label for="movie">Favorite Movie</label>
          <select id="movie" v-model="movie" name="movie">
            <option>Star Wars</option>
            <option>Vanilla Sky</option>
            <option>Atomic Blonde</option>
          </select>
        </p>
        <p>
          <input type="submit" value="Submit" />
        </p>
      </form>
    </div>
  </div>
</template>
<script>
import Modal from '~/components/Modal.vue'
export default {
  data() {
    return {
      isVisible1: false,
      isVisible2: false
    }
  },
  components: {
    Modal
  }
}
</script>
