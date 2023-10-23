<template>
    <div class="padding-wrapper" style="background-color: rgb(191, 233, 244);">
        <v-row>
            <v-col cols="4">

                <div class="category-list">

                    <div class="category blue-border" v-for="category_ in categories" :key="category_.id"
                        :style="{ backgroundColor: category_.color }">

                        <v-expansion-panels>

                            <v-expansion-panel :expand-icon="category_.icon" :collapse-icon="category_.icon"
                                :title="category_.title" :color="category_.color">

                                <v-expansion-panel-text>

                                    <div class="subtopic padding-wrapper " v-for="subtopic in category_.subtopics"
                                        :key="subtopic.id" @click="selectSubtopic(category_, subtopic)"
                                        :class="{ 'selected-subtopic': subtopic === selectedSubtopic }">

                                        <v-btn variant="tonal" :text="subtopic.title" class="ma-2"></v-btn>

                                        <v-progress-linear height="10" :model-value="subtopic.total_value"
                                            :color="category_.color" rounded>
                                        </v-progress-linear>
                                    </div>


                                </v-expansion-panel-text>

                            </v-expansion-panel>

                        </v-expansion-panels>



                    </div>
                </div>
            </v-col>
            <v-col>
                <v-card>
                    <category-details  :category="selectedCategory" :subtopic="selectedSubtopic"></category-details>

                </v-card>
            </v-col>
        </v-row>
    </div>
</template>
  
  
<script setup>
import { ref } from "vue";
import CategoryDetails from "./Categoria.vue";
import { categories_ } from "./categoriasData.js";
//import { simulateDataChanges } from "../Simulador/simulator.js";
const selectedCategory = ref(null);
const selectedSubtopic = ref(null);
const categories = categories_;

/**function toggleSubtopics(category) {
    if (category.showSubtopics) {
        // Do nothing if the clicked category is already expanded
        return;
    }

    // Close subtopics of other categories
    this.categories.forEach((cat) => {
        if (cat !== category) {
            cat.showSubtopics = false;
        }
    });

    category.showSubtopics = true;
    const activeSubtopic = category.subtopics[0];
    this.selectSubtopic(category, activeSubtopic);
}
 */
function selectSubtopic(category, subtopic) {
    this.selectedCategory = category;
    if (subtopic) {
        this.selectedSubtopic = subtopic;
    } else if (category.subtopics.length > 0) {
        this.selectedSubtopic = category.subtopics[0]; // Select the first subtopic if none is provided
    } else {
        this.selectedSubtopic = null; // No subtopics available
    }
    /**  this.$emit(
          "categorySelected",
          this.selectedCategory,
          this.selectedSubtopic
      ); */
}
</script>
<style scoped>
.category-list {
    display: flex;
    flex-direction: column;

    padding: 16px;
}

.category {
    margin-bottom: 20px;
    border: 1px solid #ccc;
    border-radius: 5px;
}

.category-header {
    display: flex;
    align-items: center;
    padding: 10px;
    cursor: pointer;
}

.category-header i {
    font-size: 24px;
    margin-right: 10px;
}

.category-title {
    font-size: 16px;
    font-weight: bold;
    margin-right: auto;
}

.subtopics {
    padding: 10px;
}

.subtopic {
    margin-bottom: 10px;
}

.subtopic-title {
    font-size: 14px;
}

.padding-wrapper {
    padding: 16px;
    border-radius: 5px;
}

.progress-label {
    font-size: 10px;
    font-weight: bold;
}

.subtopic.selected-subtopic {
    background-color: rgba(250, 250, 250, 0.2);
    /* Adjust the alpha value as needed (0.0 to 1.0) */
}
</style>
    