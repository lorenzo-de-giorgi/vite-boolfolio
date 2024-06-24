<template>
    <div class="d-flex justify-content-center align-items-center">
        <h1 class="typing-demo">Lorenzo De Giorgi</h1>
    </div>
    <div class="mt-5">
        <ProjectList />
    </div>
    
</template>

<script>
import ProjectList from './ProjectList.vue';
    export default {
        name: "AppHome",
        components: {
            ProjectList
        },
        data() {
            return {
                
            }
        },
    }
</script>

<style lang="scss" scoped>
.typing-demo {
  width: 18ch;
  animation: typing 2s steps(13), blink .5s step-end infinite alternate;
  white-space: nowrap;
  overflow: hidden;
  border-right: 3px solid;
  font-family: monospace;
  font-size: 2em;
}

@keyframes typing {
  from {
    width: 0
  }
}
    
@keyframes blink {
  50% {
    border-color: transparent
  }
}

</style>