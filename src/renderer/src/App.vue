<template>
  <div class="container-fluid d-flex flex-col m-0 p-0">
    <SideMenu @click.prevent="handleClick($event)" />
    <div class="col-9">
      <div id="interact" class="container-fluid p-1 m-0">
        <ClienteSection :opcao="currentComponent" />
        <ProdutoForm v-if="currentComponent === 'ProdutoForm'" />
        <ProdutoTable v-if="currentComponent === 'ProdutoTable'" />
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import SideMenu from './components/SideMenu.vue'
import { ProdutoForm, ProdutoTable } from './components/Produtos'
import { ClienteSection } from './components/Clientes'

const currentComponent = ref(null)
const handleClick = (event) => {
  if (event.target.id == 'cadCliente') {
    currentComponent.value = 'ClienteForm'
  }
  if (event.target.id === 'listaCliente') {
    currentComponent.value = 'ClienteTable'
  }
  if (event.target.id === 'cadProduto') {
    currentComponent.value = 'ProdutoForm'
  }
  if (event.target.id === 'listaProduto') {
    currentComponent.value = 'ProdutoTable'
  }
  // if (event.target.id === 'novaVenda') {
  //   currentComponent.value = 'VendaForm'
  // }
  // if (event.target.id === 'consultaVendas') {
  //   currentComponent.value = 'VendaTable'
  // }
}
</script>
