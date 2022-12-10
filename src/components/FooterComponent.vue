<template>

  <footer>
    <h6 class="mb-0 fw-bolder">SGT Task</h6>
    <h6 class="mb-0 fw-bolder">© Ahmed Gamal {{ new Date().getFullYear() }}</h6>
  </footer>

</template>

<script>
export default {
  name: "FooterComponent"
}
</script>

<style scoped>

footer{
  color: white;
  display: flex;
  justify-content: space-between;
  padding: 20px 50px;
  align-items: center;
}

</style>