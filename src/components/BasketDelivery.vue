<script>
import BasketCard from "./BasketCard.vue"
export default {
    name: 'BasketDelivery',
    components: {
        BasketCard,
    },
}
</script>

<template>
    <div class="BasketDelivery">
        <h2 class="title">
            Доставка:
        </h2>
        <div class="container">
            <BasketCard  title="ПЭК или СДЭК">
                <img class="img" src="@assets/Basket/pek.png" alt="">
            </BasketCard>
            <BasketCard title="Доставка по Москве и МО">
                <img class="img" src="@assets/Basket/auto.png" alt="">
            </BasketCard>
            <BasketCard title="Другие ТК">
                <img class="img" src="@assets/Basket/transparen.png" alt="">
            </BasketCard>
            <BasketCard title="Самовывоз">
                <img class="img" src="@assets/Basket/sam.png" alt="">
            </BasketCard>
        </div>  
    </div>
</template>


<style scoped>
/*-----------------------------Media---------------------*/
.BasketDelivery {
    margin: 100px 0px;
}

.title {
    margin-bottom: 40px;

    color: var(--text-dark);
    font-size: 24px;
    font-weight: 400;
    line-height: 28px;
}

.container {
    margin-bottom: 100px;
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 30px;
}
.img {
    max-width: 100%;
    max-height: 100%;
}

@media (max-width: 1280px) {}

@media (max-width: 1024px) {
    .container {
        gap: 30px;
        grid-template-columns: repeat(2, 1fr);
    }
}

@media (max-width: 768px) {
    .container {
        gap: 15px;
        grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
    }
}
</style>
