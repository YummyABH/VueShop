<script>
import BasketCard from "./BasketCard.vue"
export default {
    name: 'BasketPay',
    components: {
        BasketCard,
    },
}
</script>

<template>
    <div class="BasketPay">
        <h2 class="title">
            Оплата:
        </h2>
        <div class="container">
            <BasketCard title="Онлайн">
                <img class="img" src="@assets/Basket/card.png" alt="">
            </BasketCard>
            <BasketCard title="При получении">
                <img class="img" src="@assets/Basket/money2.png" alt="">
            </BasketCard>
        </div>  
    </div>
</template>


<style scoped>
/*-----------------------------Media---------------------*/
.BasketPay {
    margin: 100px 0px;
}
.img {
    max-width: 100%;
    max-height: 100%;
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
