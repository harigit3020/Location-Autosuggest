<template>
  <v-flex id="searchBoxContainer">
    <v-text-field
      id="searchBox"
      v-model="startlocation"
      :error-messages="errors"
      label="Start Location"
      prepend-inner-icon="mdi-map-marker"
      outlined
      rounded
      dense
    ></v-text-field>
  </v-flex>
</template>
<script type='text/javascript' src='https://www.bing.com/api/maps/mapcontrol?key=[bingmap_api_key]'></script>
<script>
export default {
  data: () => {
    return {};
  },
  metaInfo() {
    return {
      script: [
        {
          src: `https://www.bing.com/api/maps/mapcontrol?key=AmGYYu23Abpqd4GtkPhEPqUZq65EBzDmrMgUYBx_tdW3oKH4CH2TvZRcjRqbTMOV`,
          async: true,
          defer: true,
          callback: () => this.loadMapScenario(), // will declare it in methods
        },
      ],
    };
  },
  methods: {
    loadMapScenario() {
      Microsoft.Maps.loadModule("Microsoft.Maps.AutoSuggest", {
        callback: () => {
          var manager = new Microsoft.Maps.AutosuggestManager();
          manager.attachAutosuggest("#searchBox", "#searchBoxContainer");
        },
      });
    },
  },
};
</script>