<script setup lang="ts">
import { ref } from 'vue'
import { useRouter } from 'vue-router/auto'

import TheInput from '../components/TheInput.vue'

defineOptions({
  name: 'IndexPage',
})

const name = ref('')

const router = useRouter()
function go() {
  if (name.value)
    router.push(`/${encodeURIComponent(name.value)}`)
}
</script>

<template>
  <div>
    <div inline-block text-4xl i-carbon-3d-cursor />
    <p px-4 py-4 text-xl>
      <a href="https://github.com/YOYZHANG/originApp">Origin App</a>
    </p>

    <TheInput
      v-model="name"
      placeholder="What's your name?"
      autocomplete="false"
      @keydown.enter="go"
    />
    <div>
      <button m-6 text-sm :disabled="!name" @click="go">
        GO!
      </button>
    </div>
  </div>
</template>
