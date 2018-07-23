
<template>
  <div id="app">
    <div class="container">
      <div>
        <div>
          <MouseMoving/>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import MouseMoving from './components/MouseMoving.vue'

export default {
  name: 'app',
  components: {
    MouseMoving
  }
}
</script>

<style>

</style>