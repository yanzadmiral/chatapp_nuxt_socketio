<template>
  <v-row>
    <v-col class="text-center">
      <img src="/v.png" alt="Vuetify.js" class="mb-5" />
      <blockquote class="blockquote">
        &#8220;First, solve the problem. Then, write the code.&#8221;
        <footer>
          <small>
            <em>&mdash;John Johnson</em>
          </small>
        </footer>
      </blockquote>
      <v-btn
      depressed
      color="primary"
      @click="getMessage"
    >
      Primary
    </v-btn>
    </v-col>
  </v-row>
</template>

<script>
export default {
  name: 'InspirePage',
  mounted() {
    this.socket = this.$nuxtSocket({
      // nuxt-socket-io opts:
      name: 'chat', // Use socket "home"
      channel: '/index',
      // socket.io-client opts:
      reconnection: false,
    })

    this.socket
    .on('chat', (msg) => {

    })
  },
  methods: {
    async getMessage() {
      this.messageRxd = await this.socket.emit('private', { id: 'abc123' })
    },
  },
}
</script>
