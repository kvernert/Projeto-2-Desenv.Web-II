<script setup>
import { ref } from 'vue'

const produtos = ref([
  {
    id: 1,
    nome: 'CAMISETA CHRONIC 3412',
    quantidade: 0,
    preco: 89.9,
    img: 'https://static.cdnlive.com.br/uploads/707/unidade/16836471759192_zoom.jpg',
    hover: 'https://static.cdnlive.com.br/uploads/556/produto/16836472743849_detalhe.jpg',
    original: 'https://static.cdnlive.com.br/uploads/707/unidade/16836471759192_zoom.jpg'
  },
  {
    id: 2,
    nome: 'CARTEIRA CHRONIC 2022-32',
    quantidade: 0,
    preco: 89.9,
    img: 'https://static.cdnlive.com.br/uploads/707/unidade/16819155698999_zoom.jpg',
    hover: 'https://static.cdnlive.com.br/uploads/707/produto/16819155689588_zoom.jpg',
    original: 'https://static.cdnlive.com.br/uploads/707/unidade/16819155698999_zoom.jpg'
  },
  {
    id: 3,
    nome: 'CHRONIC FLEX PANEL 23/069',
    quantidade: 0,
    preco: 132.0,
    img: 'https://static.cdnlive.com.br/uploads/707/unidade/16825347673987_zoom.jpg',
    hover: 'https://static.cdnlive.com.br/uploads/707/produto/16825347668550_zoom.jpg',
    original: 'https://static.cdnlive.com.br/uploads/707/unidade/16825347673987_zoom.jpg'
  },
  {
    id: 4,
    nome: 'CHINELO CHRONIC SLIDE ROYAL REF 01',
    quantidade: 0,
    preco: 156.0,
    img: 'https://static.cdnlive.com.br/uploads/707/produto/16801142195752_zoom.jpg',
    hover: 'https://static.cdnlive.com.br/uploads/707/produto/16801142187385_zoom.jpg',
    original: 'https://static.cdnlive.com.br/uploads/707/produto/16801142195752_zoom.jpg'
  },
  {
    id: 5,
    nome: 'CAMISETA CHRONIC 3113',
    quantidade: 0,
    preco: 89.9,
    img: 'https://static.cdnlive.com.br/uploads/707/unidade/16836435697388_zoom.jpg',
    hover: 'https://static.cdnlive.com.br/uploads/707/produto/16836435689156_zoom.jpg',
    original: 'https://static.cdnlive.com.br/uploads/707/unidade/16836435697388_zoom.jpg'
  },
  {
    id: 6,
    nome: 'BONÉ BUCKET 2021/001',
    quantidade: 0,
    preco: 77.0,
    img: 'https://static.cdnlive.com.br/uploads/707/unidade/16612695019225_zoom.jpg',
    hover: 'https://static.cdnlive.com.br/uploads/707/unidade/16612695001152_zoom.jpg',
    original: 'https://static.cdnlive.com.br/uploads/707/unidade/16612695019225_zoom.jpg'
  },
  {
    id: 7,
    nome: 'CHAVEIRO FITA CHRONIC 020',
    quantidade: 0,
    preco: 29.0,
    img: 'https://static.cdnlive.com.br/uploads/707/unidade/16593795392595_zoom.jpg',
    hover: 'https://static.cdnlive.com.br/uploads/707/unidade/16593795398161_zoom.jpg',
    original: 'https://static.cdnlive.com.br/uploads/707/unidade/16593795392595_zoom.jpg'
  },
  {
    id: 8,
    nome: 'CORTA VENTO CHRONIC 2021/002V2',
    quantidade: 0,
    preco: 240.0,
    img: 'https://static.cdnlive.com.br/uploads/707/unidade/16626519642580_zoom.jpg',
    hover: 'https://static.cdnlive.com.br/uploads/707/produto/16626519631513_zoom.jpg',
    original: 'https://static.cdnlive.com.br/uploads/707/unidade/16626519642580_zoom.jpg'
  },
  {
    id: 9,
    nome: 'CAMISETA MANGA LONGA TIE DYE 017',
    quantidade: 0,
    preco: 77.0,
    img: 'https://static.cdnlive.com.br/uploads/707/unidade/16593589321625_zoom.jpg',
    hover: 'https://static.cdnlive.com.br/uploads/707/produto/16593589313257_zoom.jpg',
    original: 'https://static.cdnlive.com.br/uploads/707/unidade/16593589321625_zoom.jpg'
  },
  {
    id: 10,
    nome: 'CALÇA MOLETOM CHRONIC/DEXTER BIG 2022/011V1',
    quantidade: 0,
    preco: 120.0,
    img: 'https://static.cdnlive.com.br/uploads/707/unidade/16839072566136_zoom.jpg',
    hover: 'https://static.cdnlive.com.br/uploads/707/produto/16839072542587_zoom.jpg',
    original: 'https://static.cdnlive.com.br/uploads/707/unidade/16839072566136_zoom.jpg'
  },
  {
    id: 11,
    nome: 'BLUSA MOLETOM CHRONIC 013',
    quantidade: 0,
    preco: 331.0,
    img: 'https://static.cdnlive.com.br/uploads/707/unidade/16789029341316_zoom.jpg',
    hover: 'https://static.cdnlive.com.br/uploads/707/produto/16789029322644_zoom.jpg',
    original: 'https://static.cdnlive.com.br/uploads/707/unidade/16789029341316_zoom.jpg'
  },
  {
    id: 12,
    nome: 'SHAPE CHRONIC DE LONGBOARD 003',
    quantidade: 0,
    preco: 259.9,
    img: 'https://static.cdnlive.com.br/uploads/707/unidade/16666227623924_zoom.jpg',
    hover: 'https://static.cdnlive.com.br/uploads/707/produto/16666227602141_zoom.jpg',
    original: 'https://static.cdnlive.com.br/uploads/707/unidade/16666227623924_zoom.jpg'
  }
])
function add(index) {
  produtos.value[index].quantidade++
  totalL()
}
function subtrair(index) {
  if (produtos.value[index].quantidade > 0) {
    produtos.value[index].quantidade--
  }
  totalL()
}
let valorTotal = ref(0)

let carrinho = ref([])

function addCarrinho(produto) {
  carrinho.value.push({
    id: produto.id,
    nome: produto.nome,
    preco: produto.preco,
    quantidade: produto.quantidade,
    total: produto.preco * produto.quantidade
  })
  totalL()
  produto.quantidade = 1
}
function totalL() {
  valorTotal.value = 0
  for(const item of carrinho.value){
    valorTotal.value = valorTotal.value + item.total
  }
}

function limpaCarrinho() {
  carrinho.value = []
}
function remover(index){
  carrinho.value.splice(index, 1)
}
</script>

<template>
  <div class="bg-dark fixed-top row">
    <div class="col-md-6">
      <img
        alt="CHRONIC® "
        title="CHRONIC® "
        src="https://www.chronic420.com.br/stores/556/static/img/logo_white.png"
        class="img-responsive"
      />
    </div>
    <div class="d-flex justify-content-end col-md-6">
      <button
        type="button"
        class="btn p-3 mt-2 ml-auto"
        data-bs-toggle="modal"
        data-bs-target="#exampleModal"
      >
        🛒
      </button>
    </div>
  </div>
  <div
    class="modal fade"
    id="exampleModal"
    tabindex="-1"
    aria-labelledby="exampleModalLabel"
    aria-hidden="true"
  >
    <div class="modal-dialog modal-dialog-centered">
      <div class="modal-content">
        <div class="modal-header">
          <h1 class="modal-title fs-5" id="exampleModalLabel">Carrinho</h1>
          <button
            type="button"
            class="btn-close"
            data-bs-dismiss="modal"
            aria-label="Close"
          ></button>
        </div>
        <div class="modal-body">
          <div v-for="(item, index) in carrinho" :key="index">
            <strong> {{ item.id }} - {{ item.nome }}</strong>
            <br />
            <p>
              Preço R$ {{ item.preco }} | Quant {{ item.quantidade }} (Total: R$:{{
                item.total.toFixed(2)
              }}
              )
            </p>
          </div>
          <p v-if="carrinho.length > 0">Valor total da compra: R$ {{ valorTotal.toFixed(2) }}</p>
          <p v-else>Seu carrinho está vazio</p>
        </div>
        <div class="modal-footer">
          <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Fechar</button>
          <button @click="limpaCarrinho" type="button" class="btn btn-dark">Limpar carrinho</button>
          <button @click="remover" type="button" class="btn btn-dark">
            <i class="bi bi-trash" />
          </button>
        </div>
      </div>
    </div>
  </div>
  <div>
    <img
      src="https://static.cdnlive.com.br/uploads/556/banner/16711166388051.jpeg"
      alt="banner"
      class="banner"
    />
  </div>
  <div class="row">
    <div v-for="(item, index) in produtos" :key="index" class="col-3">
      <div class="tema">
        <b> {{ item.id }} - {{ item.nome }} </b>
        <br />
        <img
          :src="item.img"
          :hover="item.hover"
          @mouseover="item.img = item.hover"
          @mouseleave="item.img = item.original"
          class="img"
        />

        <h6>Preço: R$:{{ item.preco }}</h6>
        <h6>Quantidade: {{ item.quantidade }}</h6>

        <button type="button" @click="subtrair(index)" class="btn bg-white p-1 h-r btnW">-</button>
        <button type="button" @click="add(index)" class="btn bg-white p-1 ml-b h-g btnW">+</button>
        <button type="button" @click="addCarrinho(item)" class="btn bg-white p-1 ml-b h-g">
          Adicionar
        </button>
      </div>
    </div>
  </div>
</template>

<style scoped>
.tema {
  padding: 25px;
  width: 100%;
  margin-top: 80px;
}
.img {
  width: 231.5px;
  margin-right: 10px;
  padding: 5px;
  cursor: pointer;
}
.img-responsive {
  display: block;
  max-width: 112px;
  height: auto;
  padding: 10px;
}
.banner {
  width: 100%;
  margin-top: 60px;
}
</style>
