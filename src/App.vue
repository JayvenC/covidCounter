<template>
<Header />
<div class='container'>
  <router-view/>
</div>
</template>

<script>
import Header from '@/components/header'

export default {
  components: {
    Header
  }
}
</script>


