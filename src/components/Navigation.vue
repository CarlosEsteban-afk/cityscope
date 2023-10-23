

<template>
  <v-toolbar :elevation="5" title="CityScope Dashboard">

  </v-toolbar>

  <h3>Mesa: {{ table }}</h3>
  <v-layout>
    <v-navigation-drawer expand-on-hover rail permanent clipped>

      <v-list nav class="nav">
        <v-list-item v-for="item in items" :key="item.title" link>
          <v-list-item :title="item.title" :prepend-icon="item.icon"></v-list-item>
        </v-list-item>
      </v-list>

    </v-navigation-drawer>

  </v-layout>
</template>

<script setup>

const items = [
  { title: 'Mesa', icon: 'mdi-table-furniture' },
  { title: 'Configuración', icon: 'mdi-cog' },
  { title: 'Fórmulas', icon: 'mdi-numeric' },
  { title: 'Métricas', icon: 'mdi-puzzle-edit' },
  { title: 'Indicadores', icon: 'mdi-list-box-outline' },
];
const table = 'Temuco Centro';// New property with the desired value
const right = null;

</script>


<style>
.nav {

  flex-direction: column;
  margin-top: 10px;
  margin-left: -10px;

}
</style>