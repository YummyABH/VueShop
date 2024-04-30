<script>
import CardTool from './CardTool.vue'

export default {
    data() {
        return {
        }
    },
    name: 'VueVarieties',
    components: {
        CardTool,
    }
}
</script>

<template>
    <div class="VueVarieties">
        <div class="title">Сепараторы, конвейеры, шнековые транспортеры и линии для переработки</div>
        <div class="subtitle">Мы на связи всегда и разберемся с любыми вопросами возникшими во время эксплуатации нашего
            оборудования.</div>

        <!--------------Varieties-->
        <div class="grid-container">

            <!--------------Item-->
            <CardTool title="Станки для разделки кабеля">
                <img class="img" src="@assets/Prewie/machine.jpg" alt="">
            </CardTool>
            <CardTool title="Сепараторы">
                <img class="img" src="@assets/Varieties/machine2.png" alt="">
            </CardTool>

            <CardTool title="Станок для разделки теплообменников">
                <img class="img" src="@assets/Varieties/machine3.png" alt="">
            </CardTool>

            <CardTool title="Разделка радиаторов">
                <img class="img" src="@assets/Varieties/machine4.png" alt="">
            </CardTool>

            <CardTool title="Запасные части">
                <img class="img" src="@assets/Varieties/machine5.png" alt="">
            </CardTool>

            <CardTool title="Другое">
                <img class="img" src="@assets/Varieties/machine6.png" alt="">
            </CardTool>
            <!--------------Item End-->
        </div>
    </div>
</template>

<style scoped>
.img {
    max-height: 100%;
    max-width: 100%;
}

.VueVarieties {
    width: 100%;
    margin: 120px 0px;
}

.title {
    display: flex;
    max-width: 852px;
    font-size: 40px;
    line-height: 48px;
    margin: 20px 0px;

    color: var(--text-black, #161616);
}

.subtitle {
    display: flex;
    max-width: 852px;
    color: var(--text-hover, #757575);
    font-size: 20px;
    line-height: 24px;
    margin-top: 20px;
    margin-bottom: 60px;
}

.grid-container {
    gap: 16px;
    width: 100%;
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
}

/*--------------@media запросы*/

/*--------------1024px--------*/
@media (max-width: 1024px) {
    .VueVarieties {
        margin: 100px 0px;
    }

    .grid-container {
        grid-template-columns: 1fr 1fr;
    }
}

/*--------------768px--------*/
@media (max-width: 768px) {
    .VueVarieties {
        margin: 60px 0px;
    }

    .grid-container {
        gap: 8px;
        grid-template-columns: 1fr;
    }

    .title {
        font-size: 24px;
        line-height: 28px;
    }

    .subtitle {
        font-size: 16px;
        line-height: 16px;
    }
}
</style>