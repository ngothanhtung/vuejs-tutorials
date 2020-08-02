<template>
  <div class="container">
    <v-btn @click="increaseCount">Increase</v-btn>
    <h1>{{ this.$store.state.counter }}</h1>
    <p>{{ userAgent }}</p>
    <Message @click="click('Hello')"></Message>
  </div>
</template>

<script>
import Message from '../components/Message';
export default {
  components: {
    Message,
  },

  asyncData: ({ req }) => ({
    userAgent: req
      ? req.headers['user-agent']
      : typeof navigator !== 'undefined'
      ? navigator.userAgent
      : 'No user agent (generated)',
  }),

  methods: {
    increaseCount() {
      this.$store.commit('increment');
    },
    click(name) {
      // console.log('EMIT ON CLICK', name);
    },
  },
};
</script>
