<script>
import CardAdvantage from './CardAdvantage.vue'

export default {
    name: 'CatalogAdvantages',
    components: {
        CardAdvantage,
    },
}
</script>
    
<template>
    <div class="CatalogAdvantages">
        <div class="grid-container">
            <CardAdvantage infoTitle="Всегда на связи"
                infoText="Консультируем при покупке и в дальнейшем при эксплуатации нашего оборудования">
                <img src="@assets/Advantages/Service.png" alt="">
            </CardAdvantage>

            <CardAdvantage infoTitle="Опыт в сфере"
                infoText="Большой опыт в переработке вторсырья позволяет глубоко изучать проблемы и находить лучшие решения">
                <img src="@assets/Advantages/Case.png" alt="">
            </CardAdvantage>

            <CardAdvantage infoTitle="Наличие запчастей"
                infoText="Преимуществом производства своими силами является замена любых комплектующих и ремонт при поломке">
                <img src="@assets/Advantages/Settings.png" alt="">
            </CardAdvantage>
        </div>
    </div>
</template>
  
  
<style scoped>
.CatalogAdvantages {
    width: 100%;
    margin: 120px 0px;
}

.grid-container {
    row-gap: 32px;
    column-gap: 16px;
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
}

/*--------------@media запросы*/

/*--------------1024px--------*/
@media (max-width: 1024px) {
    .CatalogAdvantages {
        width: 100%;
        margin: 60px 0px;
    }

    .grid-container {
        grid-template-columns: 1fr 1fr;
        column-gap: 16px;
        row-gap: 32px;
    }
}

@media (max-width: 768px) {
    .CatalogAdvantages {
        width: 100%;
        margin: 40px 0px;
    }

    .grid-container {
        grid-template-columns: 1fr;
        gap: 20px;
    }
}
</style>