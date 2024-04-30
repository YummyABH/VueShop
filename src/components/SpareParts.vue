<script>
import ProductItem from './ProductItem.vue';

export default {
    data() {
        return {
        }
    },
    name: 'SpareParts',
    components: {
        ProductItem,
    },
}
</script>
    
<template>
    <div class="SpareParts">
        <div class="title">Запасные части</div>
        <div class="product__wrapper">
            <div class="product__list">
                <ProductItem Title="Звездочка для цепи" Price="600 ₽">
                    <img class="img" src="@assets/AllProducts/SpareParts/star.png" alt="">
                </ProductItem>

                <ProductItem Title="Кнопка Стопа аварийная" Price="500 ₽">
                    <img class="img" src="@assets/AllProducts/SpareParts/btn-stop.png" alt="">
                </ProductItem>

                <ProductItem Title="Рукоятка" Price="200 ₽">
                    <img class="img" src="@assets/AllProducts/SpareParts/lever.png" alt="">
                </ProductItem>

                <ProductItem Title="Нож дисковый" Price="400 ₽">
                    <img class="img" src="@assets/AllProducts/SpareParts/disk-knife.png" alt="">
                </ProductItem>
            </div>
        </div>
    </div>
</template>
  
  
<style scoped>
.img {
    max-width: 100%;
}

.SpareParts {
    margin: 60px 0px;
}

.title {
    margin-bottom: 24px;
    font-size: 24px;
    font-style: normal;
    font-weight: 400;
    line-height: 28px;
    letter-spacing: 0.24px;
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

/*-----------------------------------MEDIA ЗАПРОСЫ---------*/

@media (max-width: 1280px) {
    .product__list {
        grid-template: repeat(2, 1fr) / repeat(2, 1fr);
    }
}

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