<script setup>
import { ref } from 'vue'
import axios from 'axios';


const props = defineProps({
    name: String,
    price: Number,
})
const postRequest = async () => {
    let randomNum = Math.floor(Math.random() * (99999999 - 1) + 1);
    try {
        await axios.post(`https://de28c738d58495a7.mokky.dev/items`, {
            name: props.name,
            price: props.price,
            code: randomNum,
            quantity: 1,
        })
            .then(response => {
            })
            .catch(error => {
                console.error('Ошибка при выполнении запроса:', error);
            });
    } catch {}
}

let dataRequest = ref(0);

const availabilityСheck = async () => {
    try {
        await axios.get(`https://de28c738d58495a7.mokky.dev/items?name=` + props.name)
            .then(response => {
                const { data } = response
                dataRequest.value = data.length
                console.log(dataRequest.value);
            })
            .catch(error => {
                console.error('Ошибка при выполнении запроса:', error);
            });
    } catch {}
}


const sendingData = async () => {
    await availabilityСheck()
    if (dataRequest.value == 0) {
        return postRequest()
    }
}
</script>

<template>
    <div class="control-prewie">
        <div class="container-control">
            <div class="button-more _consultation">Проконсультироваться</div>
            <div class="button-more _basket" @click="sendingData">Добавить в корзину</div>
        </div>
        <div class="connection">
            <div class="title">Связаться со специалистом</div>
            <div class="contacts">
                <div class="number">+7 (940) 771-62-72</div>
                <div class="number">+7 (940) 925-70-88</div>
            </div>
        </div>
    </div>
</template>


<style scoped>
.control-prewie {
    display: flex;

    justify-content: space-between;
    width: 100%;
    grid-area: control;
}

.container-control {
    flex-basis: 568px;
    display: flex;
    gap: 8px;
}

.button-more {
    font-size: 16px;
    line-height: 20px;
    padding: 12px 20px;
    background: var(--text-light);
    border-radius: 8px;

    color: var(--text-dark);
}

._consultation {
    background: var(--back-button);
    color: #fff;
}

._basket {
    border: solid 1px var(--back-button);
}

.connection {
    flex-grow: 1;
}

.title {
    font-weight: 400;
    font-size: 16px;
}

.contacts {
    position: relative;
    display: flex;
    column-gap: 24px;
}

.contacts::before {
    position: absolute;
    width: 1px;
    height: 55%;
    content: '';
    background-color: rgb(233, 233, 233);
    left: calc(50% - 1px);
    top: 20%;
}

.number {
    font-weight: 400;
    font-size: 16px;
}

/*-----------------------------Media---------------------*/

@media (max-width: 1280px) {
    .control-prewie {
        margin-top: 30px;
        padding-top: 40px;
        border-top: 1px solid rgb(233, 233, 233);
    }

}

@media (max-width: 1024px) {
    .control-prewie {
        row-gap: 20px;
        flex-wrap: wrap;
    }
}

@media (max-width: 768px) {
    .control-prewie {
        padding-top: 12px;
    }

    .container-control {
        flex-wrap: wrap;
    }

    .button-more {
        padding: 10px 13px;
        font-size: 13px;
    }

    .button-more {
        text-align: center;
        width: 100%;
    }

    .contacts {
        flex-wrap: wrap;
    }
}
</style>
