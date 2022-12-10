<template>

  <section class="top-companies-section">

    <div class="container-sm py-5">

      <h4 class="text-center fw-bolder">Top Companies</h4>

      <div class="row justify-content-center px-5">

          <company-card-component

              v-for="company in companies"
              :key="company['id']"
              :companyData="company"

          ></company-card-component>

      </div>

      <div class="row mt-5">

        <div class="col-12 d-flex justify-content-center">
          <nav v-show="pagesNumber > 1">
            <ul class="pagination">
              <li class="page-item">
                <button class="page-link" :disabled="currentPage - 1 == 0 ? 'disabled' : false" @click="changePage( currentPage - 1 )"> Previous </button>
              </li>

              <li class="page-item d-flex">

                <button
                    v-for="index in pagesNumber"
                    :key="index"
                    :class="currentPage === index ? 'page-link active' : 'page-link'"
                    @click="changePage( index )"> {{ index }}
                </button>

              </li>

              <li class="page-item">
                <button class="page-link" :disabled="currentPage == pagesNumber ? 'disabled' : false" @click="changePage( currentPage + 1 )"> Next </button>
              </li>

            </ul>
          </nav>
        </div>

      </div>

    </div>

  </section>

</template>

<script>

import axios from "axios";
import CompanyCardComponent from "@/components/CompanyCardComponent";

export default {
  name: "CompaniesSectionComponent",
  components: { CompanyCardComponent },
  data () {
    return {
      companies: [],
      perPage: 3,
      currentPage: 1,
      pagesNumber : 0
    }
  },
  mounted() {
    axios
        .get(`http://127.0.0.1:8000/api/get-top-companies?per_page=${ this.perPage }&page=${ this.currentPage }`)
        .then(response => {
          this.companies   = response.data.data
          this.pagesNumber = Math.ceil( response.data.meta['total'] / this.perPage );
        })
  },
  methods: {
      changePage: function ( newPage ) {

        axios
            .get(`http://127.0.0.1:8000/api/get-top-companies?per_page=${ this.perPage }&page=${ newPage }`)
            .then(response => {
              this.companies   = response.data.data
              this.pagesNumber = Math.ceil( response.data.meta['total'] / this.perPage );
              this.currentPage = newPage;
            })
      }
  }
}
</script>

<style scoped>

.top-companies-section{
  background-color: #eee;
}

.page-link{
  color:#0075D4 !important;
}

.page-link.active{
  color:white !important;
}

</style>