<script setup lang="ts">
const error = ref('')

// import from vue use
const {
  isSupported,
  orientation,
  lockOrientation,
  unlockOrientation,
} = useScreenOrientation()

function full() {
  // only can switch the screen in full screen mode
  const element = document.documentElement // Use the root element for fullscreen

  if (element.requestFullscreen)
    element.requestFullscreen()

  // Lock to landspace
  lockOrientation('landscape').catch(e => error.value = e)
}
</script>

<template>
  <div>
    is support: {{ isSupported }} <br>
    <button mr-10 bg-red-400 px-2 py-1 @click="full">
      Rotate
    </button>
    <!-- Press to unlock -->
    <button bg-red-400 px-2 py-1 @click="unlockOrientation">
      Unlock
    </button>
    <br>
    Orentiation: {{ orientation }} <br>
    Error : {{ error }}
  </div>
</template>
