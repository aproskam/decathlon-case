<template>
  <div>
    <section class="sports vtmn-relative">
      <header
        class="
          vtmn-bg-background-brand-primary vtmn-space-y-4 vtmn-px-4 vtmn-py-8
        "
      >
        <h1 class="vtmn-typo_display-1 vtmn-text-content-primary-reversed">
          Decathlon
          <span
            v-if="sports"
            class="vtmn-typo_display-1 vtmn-text-content-primary-reversed"
            >{{ sports.length }}</span
          ><span
            v-else
            class="vtmn-typo_display-1 vtmn-text-content-primary-reversed"
            >0</span
          >
          sports challenger!
        </h1>
        <h2 class="vtmn-typo_display-2 vtmn-text-content-primary-reversed">
          Be the first to box them all!
        </h2>
      </header>

      <div
        class="
          vtmn-flex
          vtmn-content-center
          vtmn-justify-center
          vtmn-px-4
          vtmn-pt-8
          vtmn-pb-4
        "
      >
        <div class="block vtmn-sticky">
          <label class="vtmn-text-input_label" for="my-overview-input-2"
            >Search a sport</label
          >
          <div class="vtmn-text-input_container">
            <input
              type="search"
              class="vtmn-text-input"
              id="my-overview-input-2"
              placeholder="Kickbox"
              v-model="searchInput"
            />
            <span class="vtmx-search-line"></span>
          </div>
        </div>
      </div>

      <div
        v-if="sortedSports"
        class="
          sports__list
          vtmn-grid vtmn-grid-cols-2
          gt-tablet:vtmn-grid-cols-3
          vtmn-gap-2 vtmn-px-4 vtmn-pb-8
        "
      >
        <SportCard
          v-for="sport in filteredSports"
          :key="sport.id"
          :sport="sport"
          @open-modal="onOpenModal"
        />
      </div>
    </section>

    <SportModal
      v-if="showModal"
      :sport="selectedSport"
      @close-modal="onCloseModal"
    />
  </div>
</template>

<script>
import axios from "axios";
import SportCard from "./SportCard.vue";
import SportModal from "./SportModal.vue";

export default {
  name: "SportsOverview",
  data() {
    return {
      searchInput: "",
      sports: null,
      sortedSports: null,
      showModal: false,
      selectedSport: null,
    };
  },

  computed: {
    filteredSports() {
      return this.sortedSports.filter((sport) => {
        if (sport.attributes.name !== null) {
          return sport.attributes.name
            .toLowerCase()
            .includes(this.searchInput.toLowerCase());
        }
      });
    },
  },

  created() {
    const _this = this;
    const config = {
      headers: {
        "Accept-Language": "nl-nl",
        "Postman-Token": process.env.VUE_APP_Postman_Token_Sports,
        "Cache-Control": "no-cache",
      },
    };
    axios
      .get("https://sports.api.decathlon.com/sports", config)
      .then(function (response) {
        // handle success
        console.log("successfull GET", response);
        // Set raw data
        _this.sports = response.data.data;
        // Sort the sports alphabetic
        _this.sortedSports = _this.sports.sort(function (a, b) {
          if (a.attributes.name !== null) {
            return a.attributes.name.localeCompare(b.attributes.name);
          }
        });
        console.log("_this.sortedSports", _this.sortedSports);
      })
      .catch(function (error) {
        // handle error
        console.error("ERROR", error);
      });
  },

  methods: {
    onOpenModal(sport) {
      console.log("openModal", sport.id);
      this.selectedSport = sport;
      this.showModal = !this.showModal;
    },
    onCloseModal() {
      console.log("closeModal");
      this.selectedSport = null;
      this.showModal = !this.showModal;
    },
  },

  components: {
    SportCard,
    SportModal,
  },
};
</script>

<style>
/* .sports .sports__list {
  grid-template-rows: masonry;
} */
</style>
