<template>
  <button
    id="btn-close-modal-3"
    class="vtmn-btn vtmn-btn--icon-left"
    @click="toggleState"
  >
    <span
      aria-hidden="true"
      :class="`vtmx-checkbox${completed ? '' : '-blank'}-line`"
    ></span>
    Mark as done
  </button>
</template>

<script>
export default {
  name: "ButtonDone",

  data() {
    return {
      completed: false,
    };
  },
  methods: {
    toggleState() {
      console.log("toggleState");

      this.completed = !this.completed;
    },
  },
};
</script>

<style></style>
