<template>
  <div v-if="sport" class="block">
    <div class="vtmn-card vtmn-card_variant--full-image">
      <div class="vtmn-card_image">
        <img
          v-if="sport.relationships.images.data.length > 0"
          :src="sport.relationships.images.data[0].variants[0].thumbnail.url"
          :alt="sport.attributes.name"
          loading="lazy"
        />
        <img v-else src="../assets/favicon.svg" :alt="sport.attributes.name" />
      </div>

      <div class="vtmn-card_content vtmn-card_content--opaque">
        <span class="vtmn-card_content--title">
          {{ sport.attributes.name }}
        </span>
        <span
          v-if="
            sport.attributes.description !== null &&
            sport.attributes.description.length > 0
          "
          class="vtmn-card_content--body"
        >
          {{ sport.attributes.description.slice(0, 100) }}...
        </span>

        <button
          class="vtmn-btn vtmn-btn_variant--primary-reversed"
          @click="$emit('openModal', sport)"
        >
          More info
        </button>

        <ButtonDone />
      </div>
    </div>
  </div>
</template>

<script>
import ButtonDone from "./ButtonDone.vue";
export default {
  name: "SportCard",
  props: {
    sport: Object,
  },
  emits: ["openModal"],
  components: { ButtonDone },
};
</script>

<style></style>
