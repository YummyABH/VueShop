<script>
import ClientLogo from './ClientLogo.vue'

export default {
    data() {
        return {
        }
    },
    name: 'VueClients',
    components: {
        ClientLogo,
    }
}
</script>

<template>
    <div class="VueClients">

        <div class="container">
            <div class="info">
                <h1 class="info-title">Почему именно мы?</h1>
                <div class="info-text">
                    <span class="info-text-top">
                        За долгое время работы в этой области у нас более одной тысячи клиентов в базе в
                        том числе и представленные выше. В основном это компании по переработке вторсырья.
                    </span>
                    <span class="info-text-bottom">
                        Мы уже прошли тот
                        путь который вам предстоит пройти после приобретения нашей продукции и лучше подскажем: что вам
                        лучше подойдет, чего надо избегать и как более эффективно использовать то что есть.
                    </span>
                </div>
            </div>

            <div class="grid-container">
                <ClientLogo>
                    <img class="img" src="@assets/Clients/logo.png" alt="">
                </ClientLogo>
                <ClientLogo>
                    <img class="img" src="@assets/Clients/Group1.png" alt="">
                </ClientLogo>
                <ClientLogo>
                    <img class="img" src="@assets/Clients/firm.png" alt="">
                </ClientLogo>
                <ClientLogo>
                    <img class="img" src="@assets/Clients/Group2.png" alt="">
                </ClientLogo>
                <ClientLogo>
                    <img class="img" src="@assets/Clients/Group3.png" alt="">
                </ClientLogo>
                <ClientLogo>
                    <img class="img" src="@assets/Clients/fr.png" alt="">
                </ClientLogo>
            </div>
        </div>

    </div>
</template>

<style scoped>
.img {
    max-height: calc(100% - 16px);
    max-width: calc(100% - 16px);
}
.VueClients {
    width: 100%;
    margin: 120px 0px;
}

.container {
    width: 100%;
    display: flex;
    gap: 16px;
}

.info {
    border-radius: 16px;
    background: var(--back-hover, #F4F5F8);
    padding: 40px;
    box-sizing: border-box;
    width: calc(50% - 8px);
}

.info-title {
    margin-bottom: 102px;
    color: var(--text-dark, #161616);
    font-size: 40px;
    line-height: 48px;
}

.info-text {
    margin-top: 102px;
    color: var(--text-hover, #757575);
    font-size: 16px;
    line-height: 20px;
}

.info-text-top {
    display: block;
    margin-bottom: 20px;
}

.info-text-bottom {
    display: block;
    margin-top: 20px;
}

.grid-container {
    gap: 16px;
    display: grid;
    grid-template-columns: 187px 187px 187px;
    grid-template-rows: 187px 187px;
}

/*--------------@media запросы*/

/*--------------1280px--------*/
@media (max-width: 1280px) {
    .VueClients {
        width: 100%;
        margin: 100px 0px;
    }

    .grid-container {
        grid-template-columns: 1fr 1fr 1fr;
        grid-template-rows: 187px 187px;
    }

    .info {
        width: 100%;
    }

    .info-text {
        max-width: 544px;
        margin-top: 40px;
    }

    .info-title {
        max-width: 544px;
        margin-bottom: 40px;
    }

    .container {
        flex-direction: column;
    }
}

/*--------------1024px--------*/
@media (max-width: 1024px) {
    .grid-container {
        grid-template-columns: 1fr 1fr;
        grid-template-rows: 187px 187px 187px;
    }
}

/*--------------768px--------*/
@media (max-width: 768px) {
    .VueClients {
        width: 100%;
        margin: 60px 0px;
    }
    .grid-container {
        grid-template-columns: 1fr 1fr 1fr;
        grid-template-rows: 82px 82px;
        gap: 8px;
    }
    .info-title {
        margin-bottom: 12px;
        font-size: 24px;
        line-height: 28px;
    }

    .info {
        padding: 12px;
    }

    .info-text {
        margin-top: 12px;
        font-size: 14px;
        line-height: 16px;
    }

    .container {
        gap: 8px;
    }

    .info-text-top {
        margin-bottom: 10px;
    }

    .info-text-bottom {
        margin-top: 10px;
    }
}
</style>