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
  font-weight: 200;
  font-size: 0.7rem;
  padding: 2rem 0 1rem;
  text-align: center;
  /* color: #f6f3ec; */
}
</style>