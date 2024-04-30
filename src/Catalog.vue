<script>
import VueHeaderMain from './components/VueHeaderMain.vue'
import CatalogAdvantages from './components/CatalogAdvantages.vue'
import AllProducts from './components/AllProducts.vue'
import VueFooter from './components/VueFooter.vue'
import VueFeedback from './components/VueFeedback.vue'

export default {
    data() {
        return {
        }
    },
    name: 'Catalog',
    components: {
        VueHeaderMain,
        CatalogAdvantages,
        AllProducts,
        VueFooter,
        VueFeedback,
    },
}
</script>
    
<template>
    <VueHeaderMain />
    <div class="wrapper">
        <CatalogAdvantages />
        <AllProducts />
        <VueFeedback />
    </div>
    <VueFooter />
</template>
  
  
<style scoped>
.wrapper {
    max-width: 1200px;
    padding: 0px 40px;
    margin: 0 auto;
}
@media (max-width: 1024px) {
    .wrapper {
        padding: 0px 72px;
    }
}

@media (max-width: 768px) {

    .wrapper {
        padding: 0px 16px;
    }
}
</style>
  