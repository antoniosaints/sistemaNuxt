<template>
  <v-row>
    <v-col >
      <v-btn color="primary" elevation="1" to="/clientes/lista" rounded>Listar clientes</v-btn>
      <NovoCliente class="mt-4"/>
    </v-col>

  </v-row>
</template>

<script>
import NovoCliente from '@/components/clientes/NovoCliente.vue'
export default {
  name: 'InspirePage',
  data() {
    return {
     
   
    }
  },
  components: { NovoCliente },
}
</script>
