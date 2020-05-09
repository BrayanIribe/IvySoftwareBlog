<template>
    <div class="text-center bg-dark text-white mt-5 pt-4 pb-4">
        <p class="m-0 p-0">Created with ❤️ by TecPyME and IvySoftware.</p>
    </div>
</template>

<script language="ts">
import { version } from '@/../package.json'

export default {
  data () {
    return {
      version
    }
  }
}
</script>

<style lang="css" scoped>
/* Custom CSS here */

li {
    list-style: none;
}

</style>
