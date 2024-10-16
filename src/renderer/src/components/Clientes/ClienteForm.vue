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
import { ref, watch, onMounted, defineEmits } from 'vue' // Um exemplo de composição para requisições, ajuste conforme necessário

// Recebe o ID da pessoa a ser editada
const props = defineProps({
  pessoa: {
    type: Object,
    default: null
  }
})

const nome = ref('')
const email = ref('')

const emit = defineEmits(['close'])

// Função para carregar dados da pessoa para edição
const loadPessoa = () => {
  if (props.pessoa !== null) {
    nome.value = props.pessoa.nome
    email.value = props.pessoa.email
  }
}

// Carrega os dados sempre que o `pessoaId` for alterado
watch(() => props.pessoa, (newPessoa) => {
  if (newPessoa) {
    nome.value = newPessoa.nome
    email.value = newPessoa.email
  } else {
    resetForm()
  }
} )

function resetForm() {
  nome.value = ''
  email.value = ''
}

const handleClick = async (event) => {
  const formElement = document.getElementById('formCliente')

  if (event.target.id === 'btnGravar') {
    // Se `pessoaId` estiver definido, envia uma requisição `PUT` para atualizar, caso contrário, `POST` para criar novo
    const method = props.pessoa ? 'PUT' : 'POST'
    const url = props.pessoa
      ? `http://localhost:3000/pessoas/${props.pessoa.id}`
      : 'http://localhost:3000/pessoas'

    try {
      const response = await fetch(url, {
        method: method,
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
        resetForm()
        emit('close')
      } else {
        console.error('Falha ao enviar os dados', response)
        alert('Falha ao enviar os dados')
      }
    } catch (error) {
      alert('Ocorreu um erro inesperado')
      console.error('Erro:', error)
    }
  }

  if (event.target.id === 'btnLimpar') {
    formElement.reset()
    resetForm()
  }
}

// Carrega os dados da pessoa ao montar o componente
onMounted(loadPessoa)
</script>
