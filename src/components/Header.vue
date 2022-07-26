<template>
  <header class="text-center bg-blue-700 text-white p-4">
    <div class="text-2xl font-bold mb-4 md:text-4xl"> <i class="fa fa-viruses"></i> Covid-19 Tracker</div>

    <p>API by <a class="text-blue-200" href="https://covid19api.com">covid19api.com</a></p>
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
