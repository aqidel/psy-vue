<script>
export default {
  data() {
    return {
      headerStyle: false,
      scrollY: 0
    }
  },
  methods: {
    headerHandler() {
      this.headerStyle = !this.headerHandler;
    },
    handleScroll() {
      window.scrollY != 0 ? this.headerStyle = true : this.headerStyle = false;
    }
  },
  created() {
    if (process.client) {
      window.addEventListener('scroll', this.handleScroll);
    }
  },
  unmounted() {
    if (process.client) {
      window.removeEventListener('scroll', this.handleScroll);
    }
  }
}
</script>

<template>
  <header :class="{ 'header-dark' : headerStyle }" @scroll="headerHandler">
    <div class="header-content">
      <h3>Арт-терапия & Благополучие</h3>
    </div>
    <div class="header-divider" :class="{ 'header-divider-hidden' : headerStyle }">
      <hr>
    </div>
  </header>
</template>

<style scoped>
header {
  width: 100%;
  box-sizing: border-box;
  position: fixed;
  top: 0;
  transition-duration: 0.3s;
  transition-timing-function: ease;
  transition-delay: 0s;
  z-index: 100;
}

.header-dark {
  background-color: rgba(22, 22, 22, 0.9);
}

.header-content {
  padding: 24px;
}

.header-content > h3 {
  margin: 0;
  font-family: Montserrat Bold, sans-serif;
  font-size: 22px;
  line-height: 700;
  line-height: 26px;
  text-align: center;
  color: rgb(247, 247, 247);
}

.header-divider {
  width: 100%;
  box-sizing: border-box;
  padding: 0 24px;
}

.header-divider-hidden {
  display: none;
}

.header-divider > hr {
  width: 100%;
  border-color: rgba(255, 255, 255, 0.3);
  margin: 0;
}
</style>