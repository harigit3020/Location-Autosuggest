<template>
  <v-flex id="searchBoxContainer">
    <v-text-field
      id="searchBox"
      v-model="startlocation"
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
    return {startlocation:""};
  },
  metaInfo() {
    return {
      script: [
        {
          src: `https://www.bing.com/api/maps/mapcontrol?key=[bing_map apikey]`,
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