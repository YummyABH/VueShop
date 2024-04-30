<script>
import VueHeaderMain from './components/VueHeaderMain.vue'
import MyOrder from "./components/MyOrder.vue";
import BasketDelivery from './components/BasketDelivery.vue'
import BasketPay from './components/BasketPay.vue'
import ContactDetails from './components/ContactDetails.vue'
import VueFooter from './components/VueFooter.vue'

export default {
    name: 'Basket',
    components: {
        VueHeaderMain,
        MyOrder,
        BasketDelivery,
        BasketPay,
        ContactDetails,
        VueFooter,
    },
}
</script>

<template>
    <VueHeaderMain />
    <div class="wrapper">
        <div class="PlacingOrder">
            <h1 class="title">
                Оформление заказа
            </h1>
            <MyOrder />
            <BasketDelivery />
            <BasketPay />
            <ContactDetails />
        </div>
    </div>
    <VueFooter />
</template>


<style scoped>
.wrapper {
    padding: 0px 40px;
    margin: 0 auto;
    max-width: 1200px;
}

.PlacingOrder {
    border-top: 1px solid var(--dived-hover);
    padding-top: 60px;
    margin-bottom: 120px;
}

.title {
    margin-bottom: 52px;

    color: var(--text-dark);
    font-size: 40px;
    font-weight: 400;
    line-height: 48px;
}

/*-----------------------------Media---------------------*/

@media (max-width: 1280px) {}

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
