<template>
  <div class="proto has-background-primary">
    <div class="card">
      <div class="content">
        {{msg}}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Message',
  props: {
    msg: String,
  },
  data(){
    return {
    };
  },
  mounted() {
  },
  methods: {
  },
}
</script>
