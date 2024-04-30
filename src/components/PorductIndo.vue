<script>
import CardAdvantage from './CardAdvantage.vue';
import Characteristics from './Characteristics.vue'
import Video from './ProductVideo.vue'
import SpareParts from './SpareParts.vue'
import MoreProduct from './MoreProduct.vue'

export default {
    data() {
        return {
        }
    },
    name: 'ProductInfo',
    components: {
        CardAdvantage,
        Characteristics,
        Video,
        SpareParts,
        MoreProduct,
    },
}
</script>
    
<template>
        <div class="product-info">
            <!---------------------------------NAV-->
            <div class="nav">
                <div class="nav-item"><router-link :to="{hash: '#scrollDescription'}">Описание</router-link></div>
                <div class="nav-item"><router-link :to="{hash: '#scrollCharacteristics'}">Характеристики</router-link></div>
                <div class="nav-item"><router-link :to="{hash: '#scrollVideo'}">Видео</router-link></div>
                <div class="nav-item"><router-link :to="{hash: '#scrollSpare'}">Запасные части</router-link></div>
            </div>

            <div class="container">
                <!---------------------------------DESCRIPTION-->
                <div id="scrollDescription" class="description">
                    <div class="description__text">
                        <span class="text">
                            Универсальность этого станка состоит в том что на нем можно разделать не только
                            обычные кабеля в пвх изоляции, но и бронированные кабеля до 45 мм диаметром. Это возможно за
                            счет
                            редуктора
                            и небольшого оборота двигателя, ведь бронированные кабеля тяжелее прорезаются и нужно больше
                            силы на то
                            что
                            бы протянуть кабель через отверстие. На станках же с ременной передачей и быстрой скоростью
                            работы
                            бронированный кабель просто-напросто застрянет в станке.
                        </span>
                        <span class="text">На станке 7 отверстий первые два не только режут кабель но и давят. Остальные
                            отверстия
                            режут кабель с Двух
                            сторон, что облегчает работу оператора.
                        </span>

                        <span class="text">У станка есть амортизационные пружины которые давят на верхний вал. Во время
                            работы,
                            пропуская кабель через
                            отверстия верхние валы приподнимается и прорезает изоляцию. Двумя барашками сверху можно
                            регулировать
                            силу
                            давления и настроиться под определенную глубину изоляции кабеля.
                        </span>

                        <span class="text">Установлены сменные дисковые ножи которые в случае необходимости можно легко
                            заменить.
                            Так же легко заменить
                            ремни станка, это основные расходные материалы в работе со станком
                        </span>

                        <span class="text">На нем есть три кнопки: Аварийный Стоп (сверху) - нужен для мгновенной остановки
                            двигателя в случае если
                            застрял кабель или перчатку оператора затянуло в отверстие, кнопка старта и кнопка стоп.
                            Последние два
                            нужно
                            использовать в обычном режиме, Аварийный же только в крайнем случае иначе это привет
                            к его быстрому
                            износу.
                        </span>

                    </div>
                </div>

                <!---------------------------------CHARACTERISTICS-->
                <Characteristics id="scrollCharacteristics"/>

                <!---------------------------------VIDEO-->
                <Video id="scrollVideo" />
            </div>

            <!---------------------------------CARD-->
            <div class="card">
                <CardAdvantage infoTitle="Доставка по всей России"
                    infoText="Отправим товар транспортной компанией или почтовым отправлением (оплата при получении)">
                <img src="@assets/Advantages/Delivery.png" alt="">
                </CardAdvantage>
                <CardAdvantage infoTitle="Гарантия на всё"
                    infoText="Гарантия на всё Предоставляется гарантия сроком до 1 года со дня приобретения товара">
                    <img src="@assets/Advantages/Guarantee.png" alt="">
                </CardAdvantage>
            </div>
        </div>


        <!---------------------------------SPARE PARTS-->
        <SpareParts id="scrollSpare">
        </SpareParts>

        <!---------------------------------MORE PARTS-->
        <MoreProduct/>
</template>
  
  
<style scoped>

.product-info {
    display: grid;
    grid-template-columns: minmax(0px, 700px) minmax(0px, 400px);
    grid-template-rows: auto auto;
    grid-template-areas:
        "nav nav"
        "info card"
    ;
    justify-content: space-between;
    column-gap: 120px;
}

.container {
    grid-area: info;
}

.nav {
    grid-area: nav;

    display: flex;
    gap: 40px;
    margin-top: 40px;
    border-bottom: 1px solid var(--dived-hover);
}

.nav-item {
    padding-bottom: 40px;

    color: var(--text-dark);
    font-size: 16px;
    font-style: normal;
    font-weight: 400;
    line-height: 20px;
}

.description {
    margin: 60px 0px;
}

.text {
    display: block;
    margin-bottom: 25px;
}

.text:last-child {
    margin-bottom: 0px;
}

.card {
    grid-area: card;

    flex-wrap: wrap;
    margin: 60px 0px;
    display: flex;
    flex-direction: column;
    gap: 32px;
    padding: 0px;
}

@media (max-width: 1024px) {
    .product-info {
        display: grid;
        grid-template-columns: repeat(3, 100%);
        grid-template-areas:
            "card"
            "nav"
            "info"
        ;
        justify-content: space-between;
    }
    .card {
        flex-direction: row;
        justify-content: space-between;
    }
    .description {
        max-width: 600px;
    }
}

/*--------------@media запросы*/

/*--------------768px--------*/
@media (max-width: 768px) {
    .nav {
        display: none;
    }

    .description {
        font-size: 14px;
        line-height: 16px;
    }
}
</style>