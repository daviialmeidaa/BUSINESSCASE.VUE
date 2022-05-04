<template>
  <div class="tag">Posição: {{ item.Rank }}<br /></div>
  <br />
  <div class="tag-name">Nome:</div>
  {{ item.Name }}<br />
  <div class="tag-name">Plataforma:</div>
  {{ item.Platform }}<br />
  <div class="tag-name">Ano:</div>
  {{ item.Year }}<br />
  <div class="tag-name">Gênero:</div>
  {{ item.Genre }}<br />
  <div class="tag-name">Fabricante:</div>
  {{ item.Publisher }}<br />
  <div class="tag-name">Vendas na America do Norte:</div>
  {{item.NA_Sales}}<br />
  <div class="tag-name">Vendas na Europa:</div>
  {{ item.EU_Sales }}<br />
  <div class="tag-name">Vendas no Japão:</div>
  {{ item.JP_Sales }}<br />
  <div class="tag-name">Outras Vendas:</div>
  {{ item.Other_Sales }}<br />
  <div class="tag-name">Vendas Globais:</div>
  {{ item.Global_Sales }}<br />
</template>

<script>
export default {
  props: ["item"],
};
</script>

<style></style>
