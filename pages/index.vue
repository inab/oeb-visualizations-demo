<template>
  <v-container fluid>
    <v-row justify="center" align="center">
        <v-col cols="12" sm="10" md="10">  
            <v-alert
            :dark="$vuetify.theme.dark"
            dense
            border="left"
            class="text-caption mt-3"
            >

            👷🏻 OEB Visualizations is in development. New components will be progressively added and all components are subjected to changes.
            </v-alert>
            <h2>Components</h2>
            
        </v-col>
    </v-row>
    <v-row justify="center" align="center">
        <v-col cols="10" sm="10" md="10">
            <ul>
                <li v-for="component in components" :key="component.id">
                <a href="#" @click.prevent="scrollToCard(component.id)">
                    {{ component.title }}
                </a>
                </li>
            </ul>
        </v-col>

    </v-row>
    <v-row justify="center" align="center">
        <componentCard
            v-for="component in components"
            :componentToDisplay="component.component" 
            :title="component.title"
            :documentationLink="component.documentationLink"
            :id="component.id"
            />
    </v-row>
    
</v-container>
</template>

<script>
import accessibilityPlotPage from '../components/accessibilityPlotPage.vue'
import citationsPlotPage from '../components/citationsPlotPage.vue'
import componentCard from '../components/componentCard.vue'
import { data } from '../data/uptime30days.js'



export default {
  name: 'IndexPage',
  components: {
    accessibilityPlotPage,
    citationsPlotPage
  },
  data(){
    return {
      components: [
        {
            title: 'Accessibility Plot',
            id: 'accessibilityPlot',
            component: accessibilityPlotPage,
            documentationLink: 'https://inab.github.io/oeb-visualizations/components/accessibilityPlot/'
        },
        {
            title: 'Citations Plot',
            id: 'citationsPlot',
            component: citationsPlotPage,
            documentationLink: 'https://inab.github.io/oeb-visualizations/components/citationsPlot/'
        }
      ],
    }
  },
  methods: {
    scrollToCard(cardId) {
        const cardElement = document.getElementById(cardId);
        if (cardElement) {
            cardElement.scrollIntoView({ behavior: 'smooth', block: 'start' });
        }
    }
}
}
</script>


<style scoped>

.github{
  text-decoration: none;
}

</style>
