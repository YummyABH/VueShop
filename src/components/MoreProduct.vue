<script>
import CardProduct from './CardProduct.vue';

export default {
    data() {
        return {
        }
    },
    name: 'MoreProduct',
    components: {
        CardProduct,
    },
}
</script>
    
<template>
    <div class="MoreProduct">

        <div class="title">С этим товаром также смотрят</div>
        <div class="product__wrapper">
            <div class="product__list">
                <CardProduct :dataCard="{
                    name: 'S2-3 Автоматический мини',
                    weight: 13,
                    engine: 180,
                    treatment: [1.5, 25],
                    price: 34900,
                }">
                    <img src="@assets/AllProducts/prodPreview.png" alt="">
                </CardProduct>

                <CardProduct :dataCard="{
                    name: 'SG-006-1 Станок для разделки кабеля (Автоматический)',
                    weight: 13,
                    engine: 180,
                    treatment: [1.5, 25],
                    price: 34900,
                }">
                    <img src="@assets/AllProducts/prodPreview1.png" alt="">
                </CardProduct>

                <CardProduct :dataCard="{
                    name: 'SG-006-1 Станок для разделки кабеля (Автоматический)',
                    weight: 13,
                    engine: 180,
                    treatment: [1.5, 25],
                    price: 34900,
                }">
                    <img src="@assets/AllProducts/prodPreview2.png" alt="">
                </CardProduct>

                <CardProduct :dataCard="{
                    name: 'SG-006-1 Станок для разделки кабеля (Автоматический)',
                    weight: 13,
                    engine: 180,
                    treatment: [1.5, 25],
                    price: 34900,
                }">
                    <img src="@assets/AllProducts/prodPreview1.png" alt="">
                </CardProduct>
            </div>
        </div>

    </div>
</template>
  
  
<style scoped>
.title {
    margin-bottom: 24px;
    font-size: 24px;
    font-style: normal;
    font-weight: 400;
    line-height: 28px;
    letter-spacing: 0.24px;
}

.MoreProduct {
    margin: 60px 0px;
}

.product__wrapper {
    align-items: center;
    flex: 1;
    display: flex;
    flex-direction: column;
}

.product__list {
    width: 100%;
    display: grid;
    grid-template: repeat(1, 1fr) / repeat(4, 1fr);
    row-gap: 15px;
    column-gap: 16px;
}

.product__item {
    display: flex;
    flex-direction: column;
    border-radius: 16px;
    background-color: var(--back-hover);
    padding: 8px 8px 0px 8px;
}

.product__preview {
    width: 100%;
    height: 200px;
    border-radius: 12px;

    background: url(../assets/AllProducts/prodPreview.png) no-repeat center;
    background-color: var(--back-light);
}

.item__info {
    display: flex;
    flex: 1;
    flex-direction: column;
    justify-content: space-between;
    margin: 20px;
}

.item__properties {
    margin-bottom: 32px;
}

.item__title {
    margin-bottom: 8px;
    color: var(--text-dark);
    font-size: 16px;
    font-style: normal;
    font-weight: 400;
    line-height: 20px;
}

.properties__data {
    align-items: end;
    padding: 8px 0px;
    border-bottom: 1px solid var(--dived-hover);
    display: flex;
    justify-content: space-between;
    gap: 8px;
}

.data-name {
    max-width: 40%;

    color: var(--text-hover);
    font-size: 14px;
    font-style: normal;
    font-weight: 400;
    line-height: 16px;
}

.data-value {
    text-align: end;
    color: #000;
    font-size: 14px;
    font-style: normal;
    font-weight: 400;
    line-height: 16px;
}

.item__price {
    margin-top: 32px;
}

.price-item {
    color: var(--text-dark);

    font-size: 20px;
    font-style: normal;
    font-weight: 400;
    line-height: 24px;
    letter-spacing: -0.6px;
}

.price-button {
    text-align: center;
    padding: 12px 20px;
    border-radius: 8px;
    margin-top: 20px;

    background-color: var(--back-button);
    color: var(--text-light);
    font-size: 16px;
    font-style: normal;
    font-weight: 400;
    line-height: 20px;
}

/*-----------------------------------MEDIA ЗАПРОСЫ---------*/

@media (max-width: 1280px) {
    .product__list {
        grid-template: repeat(2, 1fr) / repeat(2, 1fr);
    }
}

@media (max-width: 1024px) {}

@media (max-width: 768px) {
    .title {
        font-size: 24px;
        line-height: 28px;
    }

    .product__list {
        grid-template: repeat(4, 1fr) / repeat(1, 1fr);
    }

    .item__info {
        margin: 12px;
    }
}
</style>