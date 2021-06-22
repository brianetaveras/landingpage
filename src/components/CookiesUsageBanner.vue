<template>
  <div v-if="!acceptedCookieBanner" class="cookies-usage-banner">
    <p>
      By using our site you agree to our use of cookies to deliver a better
      experience
    </p>
    <a @click.prevent="hideCookiesBanner" href="#" class="accept-cookies-btn"
      >Got it</a
    >
  </div>
</template>

<script>
export default {
  data() {
    return {
        reGatherTrigger: 0
    };
  },
  computed: {
    acceptedCookieBanner: function () {
      this.reGatherTrigger;
      const dateAccepted = window.localStorage.getItem("acceptedCookieBanner");

      if (dateAccepted) {
        return true;
      }

      return false;
    },
  },
  methods: {
    hideCookiesBanner() {
      const ISO_date = new Date().toISOString();
      window.localStorage.setItem("acceptedCookieBanner", ISO_date);
      this.reGatherTrigger++
    },
  },
};
</script>

<style >
@keyframes popOut {
  from {
    right: -100%;
  }
  to {
    right: 2%;
  }
}
.cookies-usage-banner {
  animation: popOut 1.5s;
  position: fixed;
  max-width: 400px;
  bottom: 2%;
  right: 2%;
  background: #363636;
  z-index: 99999;
  color: white;
  padding: 10px;
  border-radius: 10px;
  box-shadow: 10px 5px 10px rgba(0, 0, 0, 0.3);
}

.cookies-usage-banner a {
  color: white;
  text-decoration: underline;
}
</style>