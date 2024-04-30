<script>
export default {
    data() {
        return {
        }
    },
    props: {
        infoTitle: String,
        infoText: String,
    },
    name: 'CardAdvantage',
    components: {
    }
}
</script>

<template>
    <div class="CardAdvantage">
        <!--------------Icon-->
        <div class="container-img">
            <slot></slot>
        </div>
        <!--------------Info-->
        <div class="info">
            <div class="info__title">{{ infoTitle }}</div>
            <div class="info__text">{{ infoText }}</div>
        </div>
    </div>
</template>

<style scoped>
.CardAdvantage {
    gap: 16px;
    display: flex;
}

.container-img {
    width: 60px;
    height: 60px;
    padding: 18px;
    box-sizing: border-box;
    border-radius: 8px;
    border: 1px solid var(--dived-hover, #E9E9E9);
}

.info__title {
    margin-bottom: 8px;
    color: var(--text-dark, #161616);
    font-size: 20px;
    line-height: 24px;
    letter-spacing: -0.6px;
}

.info__text {
    margin-top: 8px;
    color: var(--text-hover, #757575);
    font-size: 16px;
    line-height: 20px;
}

/*--------------@media запросы*/

/*--------------1280px--------*/
@media (max-width: 1280px) {
}

/*--------------1024px--------*/
@media (max-width: 1024px) {
}

/*--------------768px--------*/
@media (max-width: 768px) {
    .CardAdvantage {
        gap: 12px;
    }
    .info__title {
        font-size: 16px;
        line-height: 20px;
    }

    .info__text {
        font-size: 14px;
        line-height: 16px;
    }
}
</style>