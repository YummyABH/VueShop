<script>
import CardAdvantage from './CardAdvantage.vue'

export default {
    data() {
        return {
        }
    },
    name: 'VueAdvantages',
    components: {
        CardAdvantage
    }
}
</script>

<template>
    <div class="VueAdvantages">
        <h1 class="title">Ваша рост – наш интерес, ведь тогда нам будет к чему стремиться</h1>

        <!--------------Advantages-->
        <div class="grid-container">

            <!--------------Item-->
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

            <CardAdvantage infoTitle="Доставка по всей России"
                infoText="Отправим товар транспортной компанией или почтовым отправлением (оплата при получении)">
                <img src="@assets/Advantages/Delivery.png" alt="">
            </CardAdvantage>

            <CardAdvantage infoTitle="Аренда станков" infoText="Станки можно брать на временное использование с залогом">
                <img src="@assets/Advantages/Rent.png" alt="">
            </CardAdvantage>

            <CardAdvantage infoTitle="Гарантия на всё"
                infoText="Предоставляется гарантия сроком до 1 года со дня приобретения товара">
                <img src="@assets/Advantages/Guarantee.png" alt="">
            </CardAdvantage>
        </div>
    </div>
</template>

<style scoped>
.VueAdvantages {
    width: 100%;
    margin: 120px 0px;
}

.title {
    max-width: 852px;
    margin-bottom: 60px;
    color: var(--text-dark, #161616);
    font-size: 40px;
    line-height: 48px;
}

.grid-container {
    row-gap: 40px;
    column-gap: 16px;
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
}

/*--------------@media запросы*/

/*--------------1280px--------*/
@media (max-width: 1280px) {
    .grid-container {
        row-gap: 52px;
        column-gap: 16px;
        grid-template-columns: 1fr 1fr;
    }
}

/*--------------1024px--------*/
@media (max-width: 1024px) {
    .VueAdvantages {
        margin: 100px 0px;
    }
}

/*--------------768px--------*/
@media (max-width: 768px) {
    .VueAdvantages {
        width: 100%;
        margin: 60px 0px;
    }

    .grid-container {
        gap: 20px;
        grid-template-columns: 1fr;
    }
    .title {
        font-size: 24px;
        line-height: 28px;
    }
}
</style>