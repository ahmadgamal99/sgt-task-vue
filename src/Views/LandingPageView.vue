<template>
  <div>

      <top-section></top-section>

      <companies-section-component></companies-section-component>

      <footer-component></footer-component>

  </div>
</template>

<script>

import TopSection from "@/components/TopSection";
import FooterComponent from "@/components/FooterComponent";
import CompaniesSectionComponent from "@/components/CompaniesSectionComponent";

export default {
  name: "LandingPageView",
  components: { TopSection, FooterComponent, CompaniesSectionComponent },
}
</script>
<style scoped>

</style>