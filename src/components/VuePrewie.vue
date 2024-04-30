<script setup>
import { register } from 'swiper/element/bundle';
import { onMounted, ref} from 'vue';
import axios from 'axios'
// register Swiper custom elements
register();

import { Navigation } from "swiper/modules";
import Control from './Control.vue'
import 'swiper/css/navigation';


defineProps({
    borderState: String,
    borderColor: String,
    textColor: String,
    background: String,
})

const translatedText = {
    capacity: 'Емкость',
    dimensions: 'Размеры',
    material: 'Материал',
    compatibility: 'Cовместимость',
};

function selectiveValue(value) {
    let textRes = ref('');
    for (const item in translatedText) {
        if (value == item) {
            textRes = translatedText[item];
            return textRes
        }
    }
}

let urlPage = window.location.hash;
let urlPageSearch = String(urlPage).slice(25);
let modules = [Navigation];

let item = ref([]);

onMounted(async () => {
    try {
        const { data } = await axios.get('https://cab54667e44c53ae.mokky.dev/items?id=' + urlPageSearch);
        item.value = data[0];
    } catch (err) {
        console.log(err);
    }
});
</script>

<template>
    <div class="VuePrewie">

        <!-- Страница товара -->
        <div v-if="urlPage !== '#/'" class="card" :style="{
            backgroundColor: background,
        }">
            <div class="card__wrapper">
                <!-- Info -->
                <div class="info">
                    <h1 class="title" :style="{

                        color: textColor,
                    }
                        ">{{ item.name }}</h1>
                    <div class="info__wrapper">
                        <div class="info__item" v-for="(item, key) in item.characteristics" :key="item.index" :style="{
                            borderBottomColor: borderColor,
                        }
                            ">
                            <div class="info__title">{{selectiveValue(key)}}</div>
                            <div class="info__data">{{ item }}</div>
                        </div>
                    </div>

                    <div class="info__price" :style="{
                        color: textColor,
                        borderBottomColor: borderColor,
                    }
                        ">{{ item.price }}</div>
                </div>

                <!-- View-->
                <div class="view">
                    <slot></slot>
                </div>

                <Control :name="item.name" :price="item.price" />
            </div>
        </div>

        <!-- Swiper (Главная)-->
        <swiper-container v-else class="card" slides-per-view="1" speed="500" loop="true" css-mode="false" :style="{
            backgroundColor: background,
        }" :navigation="{ nextEl: '.nextArrow', prevEl: '.prevArrow' }">

            <!-- Slide -->
            <swiper-slide class="card__wrapper">
                <!-- Info -->
                <div class="info">
                    <h1 class="title" :style="{

                        color: textColor,
                    }
                        ">{{ title }}</h1>
                    <div class="info__wrapper">
                        <div class="info__item" :style="{
                            borderBottomColor: borderColor,
                        }
                            ">
                            <div class="info__title">Диаметр обработки</div>
                            <div class="info__data">от 1,5 до 130мм </div>
                        </div>
                        <div class="info__item" :style="{
                            borderBottomColor: borderColor,
                        }
                            ">
                            <div class="info__title">Размеры</div>
                            <div class="info__data">90*68*120 см</div>
                        </div>
                        <div class="info__item" :style="{
                            borderBottomColor: borderColor,
                        }
                            ">
                            <div class="info__title">Мощность</div>
                            <div class="info__data">3 кВт 380 В</div>
                        </div>
                    </div>

                    <div class="info__price" :style="{
                        color: textColor,
                        borderBottomColor: borderColor,
                    }
                        ">209 000 ₽</div>
                </div>

                <!-- View-->
                <div class="view">
                    <slot></slot>
                </div>

                <!-- Control -->
                <div class="control">
                    <router-link :to="{ path: '/ProductPage/', query: { productId: 1}}" class="button-more">Подробнее</router-link>
                </div>
            </swiper-slide>

            <!-- Slide -->
            <swiper-slide class="card__wrapper">
                <!-- Info -->
                <div class="info">
                    <h1 class="title" :style="{

                        color: textColor,
                    }
                        ">{{ title }}</h1>
                    <div class="info__wrapper">
                        <div class="info__item" :style="{
                            borderBottomColor: borderColor,
                        }
                            ">
                            <div class="info__title">Диаметр обработки</div>
                            <div class="info__data">от 1,5 до 130мм </div>
                        </div>
                        <div class="info__item" :style="{
                            borderBottomColor: borderColor,
                        }
                            ">
                            <div class="info__title">Размеры</div>
                            <div class="info__data">90*68*120 см</div>
                        </div>
                        <div class="info__item" :style="{
                            borderBottomColor: borderColor,
                        }
                            ">
                            <div class="info__title">Мощность</div>
                            <div class="info__data">3 кВт 380 В</div>
                        </div>
                    </div>

                    <div class="info__price" :style="{
                        color: textColor,
                        borderBottomColor: borderColor,
                    }
                        ">209 000 ₽</div>
                </div>

                <!-- View-->
                <div class="view">
                    <slot></slot>
                </div>

                <!-- Control -->
                <div class="control">
                    <router-link :to="{ path: '/ProductPage/', query: { productId: 1}}" class="button-more">Подробнее</router-link>
                </div>
            </swiper-slide>
        </swiper-container>

        <!-- Arrow -->
        <div class="control__arrow" v-if="urlPage == '#/'">
            <div class="arrow prevArrow">
                <div class="arrow-left"></div>
            </div>
            <div class="arrow nextArrow">
                <div class="arrow-right"></div>
            </div>
        </div>
    </div>
</template>

<style scoped>
.info {
    display: flex;
    flex-direction: column;
    max-width: 552px;
    min-width: 552px;
    min-height: 100%;

    grid-area: info;
}

.title {
    margin: 0;
    font-style: normal;
    font-weight: 400;
    font-size: 40px;
    line-height: 48px;
    margin-bottom: 20px;
}

.info__wrapper {
    width: 450px;
}

.info__item {
    padding: 12px 0px;
    width: 100%;
    display: flex;
    justify-content: space-between;
    border-bottom: 1px solid;
}

.info__title {
    font-weight: 400;
    font-size: 16px;
    line-height: 20px;
    color: var(--text-active);
}

.info__data {
    font-weight: 400;
    font-size: 16px;
    line-height: 20px;
    color: var(--text-active);
}

.info__price {
    border-bottom: 1px solid;
    padding-bottom: 32px;
    display: flex;
    flex-direction: column;
    flex: 1 1 auto;
    justify-content: end;
    font-weight: 400;
    font-size: 24px;
    line-height: 28px;
    letter-spacing: 0.01em;
    font-feature-settings: 'liga' off;
}

.VuePrewie {
    position: relative;
    display: flex;
    width: 100%;
}

.card {
    display: flex;
    gap: 30px;
    width: 100%;

    border-radius: 16px;
    padding: 0px;
}

.view {
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 24px;
    background: var(--text-light);
    border-radius: 12px;

    grid-area: view;
}

.card__wrapper {
    min-width: 100%;
    box-sizing: border-box;
    display: grid;
    row-gap: 40px;
    column-gap: 16px;
    height: auto;
    flex-shrink: 1;

    grid-template-columns: auto 576px;
    grid-template-areas:
        "info view"
        "control control"
    ;

    justify-content: space-between;
    padding: 16px 16px 40px 40px;
}

.control {
    display: flex;
    width: 100%;
    justify-content: space-between;

    grid-area: control;
}

.button-more {
    font-size: 16px;
    line-height: 20px;
    padding: 12px 20px;
    background: var(--text-light);
    border-radius: 8px;

    color: var(--text-dark);
}

.control__arrow {
    position: absolute;
    z-index: 2;
    right: 55px;
    bottom: 40px;
    display: flex;
    gap: 8px;
}

.arrow {
    padding: 16px;
    background: var(--text-light);
    border-radius: 8px;
    display: flex;
    align-items: center;
    justify-content: center;

    &:hover {
        background-color: var(--dived-hover);
        transition-duration: 0.3s;
    }

    &:active {
        background-color: var(--back-hover);
    }
}

.arrow-left {
    width: 6.37px;
    height: 6.37px;
    border-top: 2px solid var(--text-dark);
    border-right: 2px solid var(--text-dark);
    transform: rotate(-135deg);
}

.arrow-right {
    width: 6.37px;
    height: 6.37px;
    border-top: 2px solid var(--text-dark);
    border-right: 2px solid var(--text-dark);
    transform: rotate(45deg);
}

/*--------------@media запросы*/

/*--------------1280px--------*/
@media (max-width: 1280px) {
    .card__wrapper {
        grid-template-columns: auto minmax(320px, 576px);
        grid-template-rows: 388px auto;
        row-gap: 32px;
    }

    .info {
        min-width: auto;
    }

    .control {
        padding-top: 40px;

        border-top: 1px solid var(--dived-dafault);
    }

    .info__price {
        padding-bottom: 0px;
        border-bottom: none;
    }
}

/*--------------1024px--------*/
@media (max-width: 1024px) {

    .card__wrapper {
        padding: 16px 16px 28px 16px;
        grid-template-columns: 100%;
        grid-template-rows: 380px minmax(352px, auto) auto;
        grid-template-areas:
            "view"
            "info"
            "control"
        ;
    }

    .info__item:first-child {
        padding-top: 0px;
    }

    .info__price {
        flex: 1 1 auto;
    }

    .control__arrow {
        right: 36px;
        bottom: 28px;
    }
}

/*--------------768px--------*/
@media (max-width: 768px) {
    .card__wrapper {
        row-gap: 12px;
        padding: 16px 16px 28px 16px;
        grid-template-columns: 100%;
        grid-template-rows: minmax(170px, auto) minmax(280px, auto) auto;
    }

    .card {
        height: auto;
    }

    .control {
        padding-top: 12px;
    }

    .control__arrow {
        right: 12px;
    }

    .info__wrapper {
        max-width: calc(100% - 24px);
    }

    .info__item {
        font-size: 12px;
        line-height: 16px;
    }

    .info__title {
        font-size: 12px;
        line-height: 16px;
    }

    .info__data {
        font-size: 12px;
        line-height: 16px;
    }

    .info__price {
        font-size: 18px;
        line-height: 24px;
    }

    .button-more {
        padding: 10px 13px;
        font-size: 13px;
    }

    .title {
        font-size: 24px;
        line-height: 28px;
    }
}
</style>