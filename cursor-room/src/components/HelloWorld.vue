<template>
  <div class="hello">
    <div>
      <p v-if="isConnected">We're connected to the server!</p>
      <p>Message from server: "{{ socketMessage }}"</p>
      <button @click="pingServer()">Ping Server</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      isConnected: false,
      socketMessage: ''
    }
  },
  sockets: {
    connect() {
      // Fired when the socket connects.
      this.isConnected = true;
    },

    disconnect() {
      this.isConnected = false;
    },
    // Fired when the server sends something on the "messageChannel" channel.
    messageChannel(data) {
      this.socketMessage = data
    }
  },

  methods: {
    pingServer() {
      this.$socket.emit('pingServer', 'PING!')
    }
  }
}
</script>

<style scoped>
</style>
