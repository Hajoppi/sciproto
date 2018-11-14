<template>
  <div class="home home--body">
    <router-link :to="{ name: 'main'}">
      <message msg="asd"></message>
    </router-link>
  </div>
</template>

<script>
// @ is an alias to /src
import Message from '@/components/Message';
export default {
  name: 'home',
  components: {
    Message,
  }
}
</script>
