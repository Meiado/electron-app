<script setup>
import 'bootstrap/dist/js/bootstrap.bundle.min.js'
</script>

<template>
  <div class="col-3 d-flex flex-column m-0">
    <!-- menu lateral -->
    <div id="accordionExample" class="accordion container-fluid m-0 p-0">
      <div class="accordion-item">
        <h2 id="headingOne" class="accordion-header">
          <button
            class="accordion-button"
            type="button"
            data-bs-toggle="collapse"
            data-bs-target="#collapseOne"
            aria-expanded="true"
            aria-controls="collapseOne"
          >
            Clientes
          </button>
        </h2>
        <div
          id="collapseOne"
          class="accordion-collapse collapse show"
          aria-labelledby="headingOne"
          data-bs-parent="#accordionExample"
        >
          <div class="accordion-body p-0">
            <div class="list-group">
              <button id="cadCliente" type="button" class="list-group-item list-group-item-action">
                Cadastrar
              </button>
              <button
                id="listaCliente"
                type="button"
                class="list-group-item list-group-item-action"
              >
                Consultar
              </button>
            </div>
          </div>
        </div>
      </div>
      <div class="accordion-item">
        <h2 id="headingTwo" class="accordion-header">
          <button
            class="accordion-button collapsed"
            type="button"
            data-bs-toggle="collapse"
            data-bs-target="#collapseTwo"
            aria-expanded="false"
            aria-controls="collapseTwo"
          >
            Produtos
          </button>
        </h2>
        <div
          id="collapseTwo"
          class="accordion-collapse collapse"
          aria-labelledby="headingTwo"
          data-bs-parent="#accordionExample"
        >
          <div class="accordion-body p-0">
            <div class="list-group">
              <button id="cadProduto" type="button" class="list-group-item list-group-item-action">
                Cadastrar
              </button>
              <button
                id="listaProduto"
                type="button"
                class="list-group-item list-group-item-action"
              >
                Consultar
              </button>
            </div>
          </div>
        </div>
      </div>
      <!-- <div class="accordion-item">
        <h2 id="headingThree" class="accordion-header">
          <button
            class="accordion-button collapsed"
            type="button"
            data-bs-toggle="collapse"
            data-bs-target="#collapseThree"
            aria-expanded="false"
            aria-controls="collapseThree"
          >
            Vendas
          </button>
        </h2>
        <div
          id="collapseThree"
          class="accordion-collapse collapse"
          aria-labelledby="headingThree"
          data-bs-parent="#accordionExample"
        >
          <div class="accordion-body p-0 list-group">
            <button id="novaVenda" type="button" class="list-group-item list-group-item-action">
              Nova venda
            </button>
            <button
              id="consultaVendas"
              type="button"
              class="list-group-item list-group-item-action"
            >
              Consultar
            </button>
          </div>
        </div>
      </div> -->
    </div>
  </div>
</template>
