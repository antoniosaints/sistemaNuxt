<template>
  <v-container fluid>
    <v-row>
      <v-col cols="12">
        <v-combobox
          v-model="select"
          :items="items"
          label="Selecione o pokemon"
          outlined
          dense
        ></v-combobox>
      </v-col>
      <v-col cols="12">
        <v-img :src="pokemon" width="100"> </v-img>
        {{ pokemon }}
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      pokemon: 'charmeleon',
      items: [
          'Programming',
          'Design',
          'Vue',
          'Vuetify',
        ],
    }
  },
  created() {
    this.$axios.$get('pokemon/'+this.pokemon).then(
      (response) => {
        this.pokemon = response.sprites.back_default
        console.log(response)
      },
      (error) => {
        console.log(error)
      }
    )
  },
  methods: {},
}
</script>
