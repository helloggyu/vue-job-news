<template>
  <div>
    <v-overlay :value="this.$store.state.spinnerVisible">
        <v-progress-circular
          indeterminate
          size="64"
        ></v-progress-circular>
    </v-overlay>
  </div>
</template>



<script>
export default {

}
</script>

<style>

</style>