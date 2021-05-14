<template>
  <div
    id="navbar"
    class="w-full mx-auto bg-blue-600 p-4 shadow-md"
    :class="{'opened': isNavOpen}"
  >
    <nav class="max-w-screen-2xl mx-auto flex flex-row justify-between items-center text-white">
      <div>
        <a
          href="#"
          class="flex flex-row items-center"
        >
          <img
            src="/apple.png"
            alt="SnowTricks logo"
            class="w-10 h-10"
            width="1400"
            height="1197"
          >
          <p class="pl-4 text-2xl font-bold font-jura">BileMo</p>
        </a>
      </div>

      <button
        type="button"
        class="lg:hidden w-10 h-10 flex flex-col justify-center items-center navbar-toggle cursor-pointer"
        aria-label="Open navigation menu"
        @click.prevent="toggleNav"
      >
        <span class="block w-6 h-0.5 m-1 bg-white transition ease-in-out icon-bar" />
        <span class="block w-6 h-0.5 m-1 bg-white transition ease-in-out icon-bar" />
        <span class="block w-6 h-0.5 m-1 bg-white transition ease-in-out icon-bar" />
      </button>

      <div class="navbar-menu flex flex-col items-center pt-10 md:pt-0 z-10">
        <ul class="text-center justify-center md:flex md:flex-row navbar-links font-jura font-bold">
          <li class="mb-10 sm:mb-0 transition ease-in-out">
            <a
              href="#"
              class="text-xl rounded-md px-8 sm:px-5 py-6 sm:py-3"
            >Accueil</a>
          </li>
          <li class="mb-10 sm:mb-0 transition ease-in-out">
            <a
              href="#"
              class="text-xl rounded-md px-8 sm:px-5 py-6 sm:py-3"
            >Déconnexion</a>
          </li>
        </ul>
      </div>
    </nav>
  </div>
</template>

<script>
export default {
  name: 'Nav',
  data () {
    return {
      isNavOpen: false
    }
  },
  methods: {
    toggleNav () {
      return this.isNavOpen = !this.isNavOpen
    }
  }
}
</script>

<style scoped>
#navbar.opened .navbar-toggle .icon-bar:first-child,
#navbar.opened .navbar-toggle .icon-bar:last-child {
    position: absolute;
    margin: 0;
    width: 30px;
}

#navbar.opened .navbar-toggle .icon-bar:first-child {
    transform: rotate(45deg);
}

#navbar.opened .navbar-toggle .icon-bar:nth-child(2) {
    opacity: 0;
}

#navbar.opened .navbar-toggle .icon-bar:last-child {
    transform: rotate(-45deg);
}

.navbar-menu {
    position: fixed;
    top: 4rem;
    bottom: 0;
    transition: opacity 0.2s ease-in-out,
    visibility 0.2s ease-in-out;
    opacity: 0;
    visibility: hidden;
    left: 0;
    right: 0;
    height: 25vh;
    border-bottom-left-radius: .2rem;
    border-bottom-right-radius: .2rem;
}

#navbar.opened .navbar-menu {
    background-color: #0891B2FF;
    opacity: 1;
    visibility: visible;
}

@media screen and (min-width: 1024px) {
    .navbar-toggle {
        display: none;
    }

    #navbar .navbar-menu,
    #navbar.opened .navbar-menu {
        visibility: visible;
        opacity: 1;
        position: static;
        display: block;
        height: 100%;
    }

    #navbar .navbar-links,
    #navbar.opened .navbar-links {
        margin: 0;
        padding: 0;
        box-shadow: none;
        position: static;
        flex-direction: row;
        list-style-type: none;
        max-height: max-content;
        width: 100%;
        height: 100%;
    }

    #navbar .navbar-link:last-child {
        margin-right: 0;
    }
}
</style>
