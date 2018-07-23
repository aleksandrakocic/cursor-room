<template>
  <div v-on:mousemove="sendCursorLocation" class="container">
      <img src="https://goo.gl/uRQJKR" alt="" class="cursor" v-bind:style="{ left: xCordinate + 'px', top: yCordinate + 'px' }">
  </div>
</template>

<script>

import io from 'socket.io-client';

export default {
    data() {
        return {
            yCordinate: '',
            xCordinate: '',
            socket : io('localhost:3001')
        }
    },
    methods: {
        sendCursorLocation(e) {
            this.socket.emit('sendLocation', {
                xCordinate: e.pageX, y: e.pageY
            });
        },
    },
    mounted() {
       this.socket.on('allMouseActivity', (data) => {
            console.log(data.coords);
            this.xCordinate = data.coords.x;
            this.yCordinate = data.coords.y;
        });
    },
}
</script>

<style>
.cursor {
    width: 40px;
    position: absolute;
}
.container {
    width: 100vw;
    height: 100vh;
}
</style>