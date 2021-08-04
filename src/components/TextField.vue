<template>
  <h1 class="text-3xl font-semibold md:text-5xl">
    {{ title }}
  </h1>
  <p>{{ describe }}</p>
</template>

<script>
export default {
  name: 'TextField',
  data() {
    return {
      title: 'Learn to code by watching others',
      describe: 'See how experienced developers solve problems in real-time. Watching scripted tutorials is great, but understanding how developers think is invaluable.'
    }
  }
}
</script>
