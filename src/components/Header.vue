<template>
  <header class="text-center bg-red-700 text-white p-4">
    <div class="text-2xl font-bold mb-4 md:text-4xl"> <i class="fa fa-viruses"></i> Covid-19 Tracker</div>

    <p class="italic">API by <a class="text-red-200" href="https://covid19api.com">covid19api.com</a></p>
  </header>
</template>

<script>
export default {
  name: 'Header',
  props: {
    msg: String
  }
}
</script>
