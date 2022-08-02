<template>
  <div>
    <v-btn color="primary" elevation="1" rounded class="mb-3"  to="/clientes">Novo cliente</v-btn>
    <ListaClientes />
  </div>
</template>

<script>
import ListaClientes from '~/components/clientes/ListaClientes.vue'
export default {
  name: 'Lista de clientes',
  components: { ListaClientes },
}
</script>
