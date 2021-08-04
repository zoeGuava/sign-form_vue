<template>
  <form class="flex flex-col p-6 rounded-lg shadow-grey bg-white">
    <div
      class="relative mb-4"
      :key="item.id"
      v-for="item in fieldsData ">
      <label :for="item.id"></label>
      <i v-if="item.error" :class="errorStyles.icon"></i>
      <input
        required
        :type="item.id"
        :id="item.id"
        :name="item.name"
        :value="item.value"
        v-model.trim="item.value"
        :class="[item.error ? errorStyles.input : 'focus:border-black']"
        class="p-4 mb-1 w-full border-2 rounded-md text-md font-semibold focus:outline-none focus:ring-0 focus:border-black">
      <p v-if="item.error"
        class="text-xs text-right italic text-primary-red">{{item.errorMsg}}</p>
    </div>
    <slot name="submit-section"></slot>
  </form>
</template>

<script>
export default {
  name: 'FormField',
  props: {
    'fieldsData': {
      type: Array
    },
    'errorStyles': {
      type: Object
    }
  },
  data() {
    return {
      title: 'Learn to code by watching others',
      describe: 'See how experienced developers solve problems in real-time. Watching scripted tutorials is great, but understanding how developers think is invaluable.'
    }
  }
}
</script>
