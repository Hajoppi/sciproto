<template>
    <div class="chart-card">
      <div class="content">
        {{msg}}
      </div>
    </div>
</template>

<script>
export default {
  name: 'Message',
  props: {
    msg: String,
  },
}
</script>
