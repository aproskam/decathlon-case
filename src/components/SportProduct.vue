<template>
  <li class="card-example">
    <span class="vtmn-skeleton card-example_figure"></span>
    <div class="card-example_body">
      <span class="vtmn-skeleton vtmn-skeleton_line" style="width: 95%"></span>
      <span class="vtmn-skeleton vtmn-skeleton_line" style="width: 70%"></span>
    </div>
  </li>
</template>

<script>
export default {
  name: "SportProduct",
};
</script>

<style>
.card-example {
  display: flex;
  flex-direction: column;
  width: 220px;
  box-shadow: var(--vtmn-shadow_100);
  border-radius: 8px;
  height: 200px;
  margin-bottom: var(--vtmn-spacing_6);
  background-color: var(--vtmn-semantic-color_background-primary);
}
.card-example_body {
  padding: var(--vtmn-spacing_4);
  width: 100%;
}
.card-example_figure {
  width: 100%;
  height: 100px;
  border-radius: 8px 8px 0 0;
}
</style>
