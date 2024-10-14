<template>
  <form id="formCliente" class="p-3 row g-3" @click.prevent="handleClick($event)">
    <div class="col-md-6">
      <label for="inputNome" class="form-label">Nome</label>
      <input id="inputNome" v-model="nome" type="text" class="form-control" />
    </div>
    <div class="col-md-6">
      <label for="inputEmail" class="form-label">Email</label>
      <input id="inputEmail" v-model="email" type="email" class="form-control" />
    </div>
    <div class="col-12 d-flex gap-3 justify-content-center">
      <button id="btnGravar" type="button" class="btn btn-success">Gravar</button>
      <button id="btnLimpar" type="button" class="btn btn-danger">Limpar</button>
    </div>
  </form>
</template>

<script setup>
import { ref } from 'vue'

const nome = ref('')
const email = ref('')

const handleClick = async (event) => {
  const formElement = document.getElementById('formCliente')

  if (event.target.id === 'btnGravar') {
    // Enviar uma requisição POST
    try {
      const response = await fetch('http://localhost:3000/pessoas', {
        method: 'POST',
        headers: {
          'Content-Type': 'application/json'
        },
        body: JSON.stringify({
          nome: nome.value,
          email: email.value
        })
      })

      if (response.ok) {
        console.log('Dados enviados com sucesso')
        alert('Dados enviados com sucesso')
        formElement.reset()
      } else {
        console.error('Falha ao enviar os dados', response)
        alert('Falha ao enviar os dados', response)
      }
    } catch (error) {
      alert('Ocorreu um erro inesperado')
      console.error('Erro:', error)
    }
  }

  if (event.target.id === 'btnLimpar') {
    formElement.reset()
    nome.value = ''
    email.value = ''
  }
}
</script>
