<template>
  <header>
    <div class="inner">
      <div class="logo">
        <Logo class="logo-image" />
        <span class="title">
          Nuxt sandbox project
        </span>
      </div>
      <nav>
      </nav>
    </div>
  </header>
</template>

<script>
import Logo from '~/components/Logo'

export default {
  components: {
    Logo
  },
  mounted () {
    const headerElement = document.querySelector('header')
    window.onscroll = () => {
      const doc = document.documentElement
      const scrollOffset = (window.pageYOffset || doc.scrollTop) - (doc.clientTop || 0)
      if (scrollOffset / 2 <= 16) {
        headerElement.style.boxShadow = '0 0 ' + scrollOffset / 2 + 'px rgba(0, 0, 12, .1)'
      }
    }
  }
}
</script>

<style lang="scss" scoped>
header {
  position: fixed;
  width: 100%;
  height: 54px;
  padding: 16px 0;
  top: 0;
  background-color: $white;
}
.inner,
.logo,
.logo-image {
  height: 100%;
}

.logo {
  display: flex;
  align-items: flex-end;
}

.logo-image {
  width: auto;
}

.logo span {
  display: none;
}

@media (min-width: $max-mobile) {
  .logo-image {
    margin-right: 8px;
  }
  .logo span {
    display: block;
    font-size: 24px;
    line-height: 22px;
  }
}
</style>
