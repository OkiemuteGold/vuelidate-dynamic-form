<template>
    <div id="app" class="container mx-auto py-6">
        <header>
            <div>
                <span id="logo">Liquid Gold Box</span>
            </div>
        </header>

        <div class="content">
            <FormWizard />
        </div>
    </div>
</template>

<script>
import FormWizard from "./components/FormWizard.vue";

export default {
    name: "app",
    components: {
        FormWizard,
    },
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
