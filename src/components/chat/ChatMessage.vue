<script>
export default {
  name: 'ChatMessage',

  props: {
    sent: Boolean,
    messages: Array,
    avatar: String
  }
}
</script>

<template>
  <div class="chat-message">
    <div class="flex items-end" :class="{ 'justify-end': sent }">
      <div :class="sent ? 'order-1 items-end' : 'order-2 items-start' " class="flex flex-col space-y-2 text-xs max-w-xs mx-2">
        <div v-for="(message, i) of messages" :key="i">
          <span
            v-html="message.text"
            :class="{
              [sent ? 'rounded-br-none' : 'rounded-bl-none']: i === messages.length - 1,
              'bg-gray-300 text-gray-600': !sent ,
              'bg-blue-600 text-white ': sent
            }"
            class="px-4 py-2 rounded-lg inline-block">
            {{ message.text }}
          </span>
        </div>
      </div>
      <img :class="sent ? 'order-2' : 'order-1' " class="w-6 h-6 rounded-full" :src="avatar" alt="My profile">
    </div>
  </div>
</template>

<style lang="scss">
  .chat-message {
    pre {
      @apply bg-gray-400;
      @apply px-3;
      @apply py-2;
      @apply mt-2;
      @apply rounded;
      @apply text-xs;
    }
  }
</style>
