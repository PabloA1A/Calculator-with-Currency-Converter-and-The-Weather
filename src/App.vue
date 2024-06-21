<script setup>
import Weather from './components/Weather.vue'
import Calculator from './components/Calculator.vue'
import Converter from './components/Converter.vue'

</script>

<template>

<nav>
<div>
  <Weather />
</div> 
</nav>

  <header>
    <div>
      <Calculator />
    </div>
    
  </header>

  <footer>
    <Converter />
  </footer>
    
</template>

<style lang="scss">

</style>
