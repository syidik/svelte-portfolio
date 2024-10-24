<script>
  import "../app.css";
  import Footer from "../components/Footer.svelte";
  import Hero from "../components/Hero.svelte";
  import Navbar from "../components/Navbar.svelte";
</script>



<div class="relative z-0 bg-black text-white">
  <Navbar/>
  <Hero />
  <slot />
  <Footer />
</div>

