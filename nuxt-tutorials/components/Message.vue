<template>
  <div>
    <h1>
      {{ message }}
    </h1>
    <h1>
      {{ ip }}
    </h1>
    <v-btn @click="$emit('click')">Onclick in Message Component</v-btn>
    <v-btn @click="getIp">Get IP</v-btn>
  </div>
</template>

<script>
export default {
  props: {
    message: {
      type: String,
      default: '',
    },
  },

  data: () => ({
    ip: '',
  }),

  async mounted() {
    const ip = await this.$axios.$get('http://icanhazip.com');
    this.ip = ip;
  },
  methods: {
    async getIp() {
      const ip = await this.$axios.$get('http://icanhazip.com');
      return { ip };
    },
  },
};
</script>
