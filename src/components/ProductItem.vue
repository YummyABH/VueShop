<script>
export default {
    data() {
        return {
        }
    },
    props: {
        Title: String,
        Price: String,
    },
    name: 'ProductItem',
    components: {
    },
}
</script>
    
<template>
    <div class="product__item">
        <router-link to="/ProductPage">
            <div class="product__preview">
                <slot></slot>
            </div>
        </router-link>
        <div class="item__info">
            <div class="item__properties">

                <router-link to="/ProductPage">
                    <div class="item__title">{{ Title }}</div>
                </router-link>
            </div>

            <div class="item__price">
                <div class="price-item">{{ Price }}</div>
                <router-link to="/ProductPage">
                    <div class="price-button">Купить</div>
                </router-link>
            </div>
        </div>
    </div>
</template>
  
  
<style scoped>
.product__item {
    display: flex;
    flex-direction: column;
    border-radius: 16px;
    background-color: var(--back-hover);
    padding: 8px 8px 0px 8px;
}

.product__preview {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 100%;
    height: 200px;
    border-radius: 12px;

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

@media (max-width: 768px) {
    .item__info {
        margin: 12px;
    }
}
</style>