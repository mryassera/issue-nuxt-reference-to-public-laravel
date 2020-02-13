<template>
      <v-col cols="12" sm="6" md="12" offset-sm="3">
        <v-card>
          <v-container fluid>
            <v-row>
             
              <!-- Grid images --------- -->
              <v-col v-for="n in images" :key="n.id" class="d-flex child-flex" cols="4" md="2">
                <v-card flat tile class="d-flex">
                  <v-img
                    @click="toggleDialog(`${n.name}`, 'thumbnail')"
                    :src="imageLoad(`${n.name}`, 'thumbnail')"
                    :lazy-src="imageLoad(`${n.name}`,'thumbnail')"
                    aspect-ratio="1.5"
                    class="grey lighten-2"
                  >
                  </v-img>
              <!-- ------------------- -->
  
                </v-card>
              </v-col>
            </v-row>
          </v-container>
        </v-card>
      </v-col>
  </div>
</template>

<script>

export default {
  props: ["images", "id"],
  data() {
    return {
      dialog: false,
      selectedImage: "logo.jpg"
    };
  },
  methods: {
    imageLoad(item, folder) {
      try {
        return require(`~/../public/images/${folder}/${this.id}/${item}`);
      } catch (error) {
        return require(`~/../public/images/logo.jpg`);
      }
    },
    toggleDialog(url) {
      this.selectedImage = url;
      this.dialog = true;
    }
  },
};
</script>
