<script setup>
import { onMounted, ref } from 'vue';
import axios from 'axios'
const props = defineProps({
    dataCard: Object,
})
const numQuantity = ref(props.dataCard.quantity)
const idItem = props.dataCard.id
const dataPatch = async (num) => {
    if ((numQuantity.value + num) > 0) { 
        await axios.patch(`https://de28c738d58495a7.mokky.dev/items/${props.dataCard.id}`, {
            quantity: +numQuantity.value + num,
        })
        .then(response => {
            numQuantity.value = response.data.quantity
        })
        .catch(error => {
            console.log(error);
        })
    }
}



</script>

<template>
    <div class="container-item">
        <div class="item-order">
            <div class="container-img">
                <img src="../assets/AllProducts/prodPreview1.png" class="img">
            </div>


        </div>
        <div class="check">
            <div class="data">
                <div class="item-title">{{ props.dataCard.name }}</div>
                <div class="code">Код: {{ props.dataCard.code }}</div>
            </div>
            <div class="check-container">
                <div class="counter">
                    <div class="button-plus" @click="dataPatch(1), $emit('arrDataQuantity', numQuantity + 1, idItem)"></div>
                    <div class="counter-item">{{ numQuantity }}</div>
                    <div class="button-minus" @click="dataPatch(-1), $emit('arrDataQuantity', numQuantity - 1, idItem)"></div>
                </div>
                <div class="price">{{ props.dataCard.price }} ₽</div>
                <div class="delete" @click="$emit('deleteProduct', idItem)">
                    <svg enable-background="new 0 0 40 40" id="Слой_1" version="1.1" viewBox="0 0 40 40"
                        xml:space="preserve" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
                        <g>
                            <path
                                d="M28,40H11.8c-3.3,0-5.9-2.7-5.9-5.9V16c0-0.6,0.4-1,1-1s1,0.4,1,1v18.1c0,2.2,1.8,3.9,3.9,3.9H28c2.2,0,3.9-1.8,3.9-3.9V16   c0-0.6,0.4-1,1-1s1,0.4,1,1v18.1C33.9,37.3,31.2,40,28,40z" />
                        </g>
                        <g>
                            <path
                                d="M33.3,4.9h-7.6C25.2,2.1,22.8,0,19.9,0s-5.3,2.1-5.8,4.9H6.5c-2.3,0-4.1,1.8-4.1,4.1S4.2,13,6.5,13h26.9   c2.3,0,4.1-1.8,4.1-4.1S35.6,4.9,33.3,4.9z M19.9,2c1.8,0,3.3,1.2,3.7,2.9h-7.5C16.6,3.2,18.1,2,19.9,2z M33.3,11H6.5   c-1.1,0-2.1-0.9-2.1-2.1c0-1.1,0.9-2.1,2.1-2.1h26.9c1.1,0,2.1,0.9,2.1,2.1C35.4,10.1,34.5,11,33.3,11z" />
                        </g>
                        <g>
                            <path
                                d="M12.9,35.1c-0.6,0-1-0.4-1-1V17.4c0-0.6,0.4-1,1-1s1,0.4,1,1v16.7C13.9,34.6,13.4,35.1,12.9,35.1z" />
                        </g>
                        <g>
                            <path
                                d="M26.9,35.1c-0.6,0-1-0.4-1-1V17.4c0-0.6,0.4-1,1-1s1,0.4,1,1v16.7C27.9,34.6,27.4,35.1,26.9,35.1z" />
                        </g>
                        <g>
                            <path
                                d="M19.9,35.1c-0.6,0-1-0.4-1-1V17.4c0-0.6,0.4-1,1-1s1,0.4,1,1v16.7C20.9,34.6,20.4,35.1,19.9,35.1z" />
                        </g>
                    </svg>
                </div>
            </div>
        </div>
    </div>
</template>


<style scoped>
.check-container {
    display: flex;
    flex: 0 0 auto;
    align-items: center;
    gap: 20px;

}

.container-item {
    border-top: 1px solid var(--dived-hover);
    border-bottom: 1px solid var(--dived-hover);
    max-width: 100%;
    padding: 25px 0px;
    display: flex;
    align-items: center;
    gap: 20px;
}

.delete {
    border-radius: 8px;
    border: 1px solid var(--text-active);
    display: inline-block;
    padding: 10px;
    height: 24px;
    width: 24px;
}

.item-order {
    display: flex;
    gap: 20px;
    align-items: center;
}

.container-img {
    width: 200px;
}

.item-title {
    margin-bottom: 10px;

    font-size: 20px;
    font-weight: 400;
    line-height: 24px;
}

.check {
    flex: 1 1 auto;
    display: flex;
    justify-content: space-between;
    align-items: center;
    gap: 40px;
}

.counter {
    display: flex;
    align-items: center;
    column-gap: 8px;
}

.button-plus {
    position: relative;
    height: 24px;
    width: 24px;
}

.button-plus::after {
    position: absolute;
    width: 16px;
    height: 2px;
    top: 50%;
    left: 4px;
    background-color: var(--text-active);
    content: "";
}

.button-plus::before {
    position: absolute;
    width: 16px;
    height: 2px;
    top: 50%;
    left: 4px;
    background-color: var(--text-active);
    content: "";
    transform: rotate(-90deg);
}

.button-minus {
    position: relative;
    height: 24px;
    width: 24px;
}

.button-minus::after {
    position: absolute;
    width: 16px;
    height: 2px;
    top: 50%;
    left: 4px;
    background-color: var(--text-active);
    content: "";
}

.counter {
    font-size: 16px;
    font-weight: 400;
    line-height: 20px;
}

.counter-item {
    text-align: center;
    width: 24px;
    height: 24px;
    border: 2px solid var(--text-dark);
}

.price {
    font-size: 20px;
    font-weight: 400;
    line-height: 24px;
}

/*-----------------------------Media---------------------*/

@media (max-width: 1280px) {}

@media (max-width: 1024px) {
    .check {
        flex-direction: column;
        align-items: flex-start;
        gap: 20px;
    }
}

@media (max-width: 768px) {
    .check {
        row-gap: 12px;
    }

    .container-img {
        width: auto;
        max-width: 150px;
    }

    .check-container {
        row-gap: 15px;
        flex-wrap: wrap;
    }

    .price {
        font-size: 14px;
        line-height: 18px;
    }

    .item-title {
        font-size: 12px;
        line-height: 16px;
    }

    .counter {
        order: 2;
    }

    .button-minus {
        height: 20px;
        width: 20px;
    }

    .button-minus::after {
        width: 16px;
        left: 2px;
    }

    .button-plus {
        height: 20px;
        width: 20px;
    }

    .button-plus::after {
        width: 16px;
        left: 2px;
    }

    .button-plus::before {
        width: 16px;
        left: 2px;
    }

    .counter-item {
        width: 20px;
        height: 20px;
    }

    .delete {
        order: 3;
        width: 16px;
        height: 16px;
        padding: 8px;
    }
}
</style>
