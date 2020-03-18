<template>
  <div class="app-header">
    <div>
      <span class="logo"
        >F<i class="fas fa-apple-alt"></i
        ><i class="fas fa-hamburger"></i>DIE</span
      >
    </div>

    <div class="contact-wrapper">
      <span class="contact">
        <i class="far fa-envelope"></i>
        <a href="mailto:davidisrael194@gmail.com" target="_top">
          davidisrael194@gmail.com</a
        >
      </span>

      <span class="contact">
        <i class="fas fa-phone-volume"></i>
        <a href="tel:+2349064688408">+2349064688408</a>
      </span>
    </div>
  </div>
</template>

<script>
export default {
  name: "Header"
};
</script>

<style scoped>
@media screen and (min-width: 780px) {
  .app-header {
    /* background: #fbd791; */
    color: rgb(21, 99, 99);
    display: flex;
    justify-content: space-between;
    align-items: center;
    flex-wrap: wrap;
    padding-bottom: 1em;
  }

  .logo {
    font-size: 2em;
    letter-spacing: 7px;
    font-weight: bold;
  }

  .contact-wrapper {
    display: flex;
    align-items: center;
    flex-wrap: wrap;
  }

  .contact-wrapper span:nth-of-type(1) {
    padding-right: 2em;
  }

  .contact {
    font-size: 0.9em;
  }

  .contact a:hover {
    text-decoration: underline;
  }
}

@media screen and (max-width: 780px) {
  .app-header {
    color: rgb(21, 99, 99);
    padding-bottom: 1em;
    letter-spacing: 3px;
    font-weight: bold;
    font-size: 1.5em;
  }

  .contact-wrapper {
    display: none;
  }
}
</style>
