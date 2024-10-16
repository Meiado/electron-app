<template>
  <div v-if="!alterando" class="container p-3">
    <input type="text" class="form-control" placeholder="Search" @input="handleSearch($event)" />
    <table class="mt-2 table table-hover">
      <thead>
        <tr>
          <th scope="col">#</th>
          <th scope="col">Nome</th>
          <th scope="col">Email</th>
          <th scope="col"></th>
          <th scope="col"></th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="pes in filteredPessoas" :key="pes.id">
          <td>{{ pes.id }}</td>
          <td>{{ pes.nome }}</td>
          <td>{{ pes.email }}</td>
          <td><button @click="alterarPessoa(pes.id)">Alterar</button></td>
          <td><button @click="excluirPessoa(pes.id)">Excluir</button></td>
        </tr>
      </tbody>
    </table>
  </div>
  <ClienteForm v-if="alterando" :pessoa="pessoa.value" @close="alterando = false" />
</template>

<script setup>
import { onMounted, ref, computed } from 'vue'
import { ClienteForm } from './'

const pessoas = ref([])
const alterando = ref(false)
const pessoa = ref(null)
const searchTerm = ref('')

async function loadPessoas() {
  try {
    const response = await fetch('http://localhost:3000/pessoas', {
      method: 'GET',
      headers: {
        'Content-Type': 'application/json'
      }
    })

    if (!response.ok) {
      alert('Erro ao buscar dados, ' + response.status)
      throw new Error('Erro ao buscar dados, ' + response.status)
    }

    const json = await response.json()
    pessoas.value = json.data
  } catch (error) {
    console.error('Erro na requisição:', error)
    alert('Erro na requisição: ' + error.message)
  }
}

function alterarPessoa(id) {
  alterando.value = true
  pessoa.value = pessoas.value.find((p) => p.id === id)
}

async function excluirPessoa(id) {
  // console.log('Excluir pessoa com ID:', id)
  try {
    const response = await fetch('http://localhost:3000/pessoas/' + id, {
      method: 'DELETE',
      headers: {
        'Content-Type': 'application/json',
      }
    })

    if (!response.ok) {
      alert('Erro ao exlcuir, ' + response.status)
      throw new Error('Erro ao excluir, ' + response.status)
    }

    const json = await response.json()
    alert(json.message)
    await loadPessoas()
  } catch (error) {
    console.error('Erro na requisição:', error)
    alert('Erro na requisição: ' + error.message)
  }
}

const filteredPessoas = computed(() => {
  return pessoas.value.filter((pessoa) => {
    return (
      pessoa.nome.toLowerCase().includes(searchTerm.value.toLowerCase()) ||
      pessoa.email.toLowerCase().includes(searchTerm.value.toLowerCase())
    )
  })
})

function handleSearch(event) {
  searchTerm.value = event.target.value
}

onMounted(() => {
  loadPessoas()
})
</script>
