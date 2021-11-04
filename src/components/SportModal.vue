<template>
  <div class="vtmn-modal show" id="vtmn-modal" aria-hidden="false">
    <div id="vtmn-modal-background" class="vtmn-modal_background-overlay"></div>

    <div class="vtmn-modal_content">
      <div class="vtmn-modal_content_title">
        <p class="vtmn-modal_content_title--text">
          {{ sport.attributes.name }}
        </p>
        <button
          @click="$emit('closeModal')"
          id="btn-close-modal-1"
          class="
            vtmn-btn
            vtmn-btn_variant--ghost
            vtmn-btn_size--small
            vtmn-btn--icon-alone
          "
          aria-label="close"
        >
          <span class="vtmx-close-line"></span>
        </button>
      </div>
      <div class="vtmn-modal_content_body">
        <p
          v-if="sport.attributes.description"
          class="vtmn-modal_content_body--text"
        >
          {{ sport.attributes.description }}
        </p>

        <ButtonDone />

        <div class="vtmn-my-4">
          <p class="vtmn-modal_content_title--text vtmn-py-4">
            Sport equipment
          </p>

          <ul class="list-example vtmn-flex">
            <SportProduct v-for="index in 4" :key="index"></SportProduct>
          </ul>
        </div>

        <div class="vtmn-mt-4 vtmn-mb-8">
          <p class="vtmn-modal_content_title--text vtmn-py-4">Sport places</p>

          <div
            v-if="loading"
            class="vtmn-loader vtmn-loader_size--medium"
          ></div>

          <div v-if="sportPlaces !== null && sportPlaces.length > 0">
            <ul>
              <li
                v-for="place in sportPlaces"
                :key="place.properties.uuid"
                class="vtmn-typo_text-1 vtmn-py-4"
              >
                {{ place.properties.name }}
                <span
                  >Coordinates:
                  <span
                    class="block"
                    v-for="coordinate in place.geometry.coordinates"
                    :key="coordinate"
                    >{{ coordinate }},
                  </span>
                </span>
              </li>
            </ul>
          </div>
          <div
            v-else-if="sportPlaces !== null && sportPlaces.length === 0"
            class="vtmn-typo_text-1"
          >
            No sport places found
          </div>
        </div>

        <div class="vtmn-modal_content_actions">
          <ButtonDone />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import SportProduct from "./SportProduct.vue";
import ButtonDone from "./ButtonDone.vue";

export default {
  name: "SportModal",
  data() {
    return {
      sportPlaces: null,
      loading: true,
    };
  },
  created() {
    const _this = this;
    const config = {
      headers: {
        "Postman-Token": process.env.VUE_APP_Postman_Token_Places,
        "Cache-Control": "no-cache",
      },
    };
    // Get sport places data based on current sport id
    axios
      .get(
        `https://sportplaces.api.decathlon.com/api/v1/places?country=NL&sports=${this.sport.id}`,
        config
      )
      .then(function (response) {
        // handle success
        console.log("successfull GET sport place", response);
        _this.sportPlaces = response.data.data.features;
        _this.loading = !_this.loading;
      })
      .catch(function (error) {
        // handle error
        console.error("ERROR", error);
      });
  },
  props: {
    sport: Object,
  },
  emits: ["closeModal"],
  components: { SportProduct, ButtonDone },
};
</script>

<style></style>
