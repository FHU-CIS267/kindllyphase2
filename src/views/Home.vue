<template>
  <div class="home">
    <main>
      <Discover/>
      <MyKindllys/>
    </main>
    
  </div>
</template>

<script>
import Discover from '@/components/Discover.vue'
import MyKindllys from '@/components/MyKindllys.vue'


export default {
  name: 'Home',
  components: {
    Discover,
    MyKindllys
  }
}
</script>

<style scoped>

main {
  display: flex;
	min-height: 75vh;
	margin: 6rem auto 0;
  max-width: 900px;
}

</style>