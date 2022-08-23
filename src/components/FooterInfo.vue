<template>
  <footer>
    <div
      class="
        max-w-7xl
        mx-auto
        px-2
        sm:px-6
        lg:px-8
        footer
        text-white
        md:flex
        container
        py-6
        mx-auto
      "
    >
      <div class="md:w-1/4 text-center md:text-left p-4 md:p-0">
        <h4 class="font-bold">ADDRESS:</h4>
        <p>
          Second Floor<br />
          James Williams house<br />
          9 Museum Pl<br />
          Cardiff<br />
          CF10 3BD
        </p>
      </div>
      <div class="md:w-1/4 text-center md:text-left p-4 md:p-0">
        <h4 class="font-bold">EMAIL:</h4>
        <p>example@sotic.net</p>
        <h4 class="font-bold md:mt-6">TELEPHONE:</h4>
        <p>020 123 456</p>
      </div>
      <div class="md:w-1/2 text-center md:text-left p-4 md:p-0">
        <h4 class="font-bold">SIGN UP:</h4>
        <input
          type="text"
          class="text-gray-500 p-2 w-1/2 text-sm"
          name="newsletter"
          placeholder="Your Email"
        /><button class="px-4 py-2 newsletter-button">Sign Up</button>
      </div>
    </div>
  </footer>
</template>

<script>
export default {
  name: "FooterInfo",
};
</script>

<style scoped>
footer {
  background-color: #445b7c;
}
.newsletter-button {
  background-color: #284b63;
}
</style>