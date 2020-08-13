<template>
    <footer class="footer-box-bottom">
            <p>© {{ new Date().getFullYear() }} - All Rights Reserved</p>
    </footer>
</template>

<script>
export default {
    name: 'Footer'
}
</script>

<style>
footer {
  font-family: 'Nunito', sans-serif;
  font-size: 200;
  padding: 2rem 5rem;
  text-align: center;
  /* color: #f6f3ec; */
}
</style>