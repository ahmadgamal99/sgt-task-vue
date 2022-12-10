<template>

  <div class="col-md-4 col-12 mt-4">
    <div class="card text-black">
      <div class="card-image">
        <img :src="company['logo']"
             class="card-img-top" alt="company" height="300" width="300"/>
      </div>
      <div class="card-body">
        <div class="text-center">
          <h4 class="card-title">{{ company['name'] }}</h4>
        </div>
        <div>
          <div class="d-flex justify-content-between mt-4 fw-bolder">
            <span>Revenue</span><span>{{ company['revenue'] + ' EGP'}}</span>
          </div>
        </div>
      </div>
    </div>
  </div>

</template>

<script>
export default {
  name: "CompanyCardComponent",
  props: [ 'companyData' ],
  data () {
    return {
      company: null
    }
  },
  mounted() {
    this.company = this.companyData;
  }
}
</script>

<style scoped>

.card-image{
  padding: 2rem;
}

</style>