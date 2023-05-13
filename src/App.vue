<scrip setup>
import { ref } from 'vue'

const mercadoria = ref([
  {
    id: 1,
    nome: 'CAMISETA CHRONIC 3412',
    quantidade: 0,
    preco: 89.90
  },
  {
    id: 2,
    nome: 'CARTEIRA CHRONIC 2022-32',
    quantidade: 0,
    preco: 89.90
  },
  {
    id: 3,
    nome: 'CHRONIC FLEX PANEL 23/069',
    quantidade: 0,
    preco: 132.00
  },
  {
    id: 4,
    nome: 'CHINELO CHRONIC SLIDE ROYAL REF 01',
    quantidade: 0,
    preco: 156.00
  },
  {
    id: 5,
    nome: 'CAMISETA CHRONIC 3113',
    quantidade: 0,
    preco: 89.90
  },
  {
    id: 6,
    nome: 'BONÉ BUCKET 2021/001',
    quantidade: 0,
    preco: 77.00
  },
  {
    id: 7,
    nome: 'CHAVEIRO FITA CHRONIC 020',
    quantidade: 0,
    preco: 29.00
  },
  {
    id: 8,
    nome: 'CORTA VENTO CHRONIC 2021/002V2',
    quantidade: 0,
    preco: 240.00
  },
  {
    id: 9,
    nome: 'CAMISETA MANGA LONGA TIE DYE 017',
    quantidade: 0,
    preco: 77.00
  },
  {
    id: 10,
    nome: 'CALÇA MOLETOM CHRONIC/DEXTER BIG 2022/011V1',
    quantidade: 0,
    preco: 120.00
  },
  {
    id: 11,
    nome: 'BLUSA MOLETOM CHRONIC 013',
    quantidade: 0,
    preco: 331.00
  },
  {
    id: 12,
    nome: 'SHAPE CHRONIC DE LONGBOARD 003',
    quantidade: 0,
    preco: 259.90
  }
])

const enviou = ref(false)

const carrinho = ref({
  items: [],
  total: 0
  


  
  function adicionarCarrinho(mercadoria) {
    carrinho.value.items.push({
      id: mercadoria.id,
      nome: mercadoria.nome,
      preco: mercadoria.preco,
      quantidade: mercadoria.quantidade,
      total: mercadoria.preco * mercadoria.quantidade
    })
    carrinho.value.total += mercadoria.preco * mercadoria.quantidade
  }
})

function adiciona(index) {
  mercadoria.value[index].quantidade++
  const pos = carrinho.value.items.indexOf(
    carrinho.value.items.find((c) => c.id === mercadoria.value[index].id)
  )
  if (pos != -1) {
    carrinho.value.total -= carrinho.value.items[pos].total
    carrinho.value.items[pos].total =
      ++carrinho.value.items[pos].quantidade * carrinho.value.items[pos].preco
      carrinho.value.total += carrinho.value.items[pos].total
      function adicionarCarrinho(mercadoria) {
        carrinho.value.items.push({
          id: mercadoria.id,
          nome: mercadoria.nome,
          preco: mercadoria.preco,
          quantidade: mercadoria.quantidade,
          total: mercadoria.preco * mercadoria.quantidade
        })
        carrinho.value.total += mercadoria.preco * mercadoria.quantidade
      }
  }
}

function subtrai(index) {
  if (mercadoria.value[index].quantidade > 0) {
    mercadoria.value[index].quantidade--
  }
  const pos = carrinho.value.items.indexOf(
    carrinho.value.items.find((c) => c.id === mercadoria.value[index].id)
  )
  if (pos != +1) {
    carrinho.value.total -= carrinho.value.items[pos].total
    carrinho.value.items[pos].total =
      --carrinho.value.items[pos].quantidade * carrinho.value.items[pos].preco
      carrinho.value.total += carrinho.value.items[pos].total
  }
}

function limparCarrinho() {
  carrinho.value.items = 0
  carrinho.value.total = 0
}

</script>

<template>
  <div>
    <nav>
      <button @click="enviou =! enviou">🛒</button>
    <div v-if="enviou" class="modal fade" id="exampleModal" tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true">
      <div class="modal-dialog modal-dialog-centered">
        <div class="modal-content">
          <div class="modal-header">
            <h1 class="modal-title fs-5" id="exampleModalLabel">Carrinho</h1>
            <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
          </div>
          <div class="modal-body">
            <div v-for="(itemDoCarrinho, index) in carrinho.items" :key="itemDoCarrinho.id">
            <strong> {{ itemDoCarrinho.id }} - {{ itemDoCarrinho.nome }}</strong>
            <br>
            <p>Preço R$ {{itemDoCarrinho.preco }} | Quant {{ itemDoCarrinho.quantidade}} (Total: {{ itemDoCarrinho.total }} )</p>
          </div>
          <p v-if="carrinho.length > 0">Valor total da compra: R$ {{ carrinho.total }}</p>
          <p v-else></p>
          </div>
          <div class="modal-footer">
            <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Fechar</button>
            <button @click="limparCarrinho" type="button" class="btn btn-warning">Limpar carrinho</button>
          </div>
        </div>
      </div>
    </div>
    </nav>

      <div v-for="(mercadoria, index) in mercadoria" :key="mercadoria.id">
        <div>
          <b> {{ mercadoria.id }} - {{ mercadoria.nome }} </b>
          <h6>Preço: R$:{{ mercadoria.preco }}</h6>
          <h6>Quantidade: {{ mercadoria.quantidade }}</h6>

          <button type="button" @click=" subtrai(index)" >-</button>
          <button type="button" @click="adiciona(index)">+</button>
          <button type="button" @click="adicionarCarrinho(mercadoria)">Adicionar</button>
        </div>
      </div>
    </div>
  </template>


<style scoped>

</style>
