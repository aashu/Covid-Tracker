<template>
  <Header />
  <div class="container">
    <router-view/>
    </div>
</template>

<script>
import Header from "@/components/Header"
import './assets/tailwind.css'
export default {
  components: {
    Header
  }
}
</script>
