
<template>
    <div class="full-width-container">
        <v-card class="full-width-card">
            <v-tabs v-model="tab" bg-color="deep-purple" align-tabs="center">
                <v-tab href="#CityScope">
                    Categorias
                    <v-icon>mdi-chart-areaspline</v-icon>
                </v-tab>
                <v-tab href="#Radar">
                    Radar
                    <v-icon>mdi-radar</v-icon>
                </v-tab>
            </v-tabs>

            <v-card-text>
                <v-window v-model="tab">
                    <v-window-item value="#CityScope">
                        <Cont class="padding-wrapper" />
                    </v-window-item>

                    <v-window-item value="#Radar">
                        <Radar class="padding-wrapper" />
                    </v-window-item>

                </v-window>
            </v-card-text>
        </v-card>

    </div>
</template>
    
<script setup>
import Radar from "@/components/Radar/Radar.vue";
import Cont from "@/components/Categorias/ListaCategorias.vue";
import { ref } from "vue";

const tab = ref(null);

</script>
    
<style>
.padding-wrapper {
    padding: 16px;
}

.full-width-container {
    width: 100%;
    /* Make the container take the full width of the page */


}

.full-width-card {
    width: 100%;
    /* Make the card take the full width of the container */



}

.full-width-tabs {
    width: 100%;
    /* Make the tabs component take the full width of the card */


}
</style>