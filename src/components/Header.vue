<template>
  <header>
    <p>WHAT NEEDS TO BE DONE?</p>
  </header>
</template>

<script lang="ts">
import { Options, Vue } from "vue-class-component";

export default class Header extends Vue {}
</script>

<style>
header {
  margin-bottom: 50px;
  height: 100px;
  display: flex;
  justify-content: center;
  align-items: center;
  font-family: monospace, "Courier New", Courier;
  font-size: 30pt;
  font-weight: bold;
  color: #22b455;
  text-align: center;
}
</style>
