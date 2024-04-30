<script>
export default {
    data() {
        return {
        }
    },
    props: {
        title: String,
    },
    name: 'CardTool',
    components: {
    },
}
</script>

<template>
    <div class="CardTool">
        <div class="item-title">{{ title }}</div>
        <div class="container-img">
            <slot></slot>
        </div>
    </div>
</template>

<style scoped>
.CardTool {
    padding: 24px;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    border-radius: 16px;
    background: var(--back-hover, #F4F5F8);
}

.item-title {
    width: 100%;
    font-size: 24px;
    line-height: 28px;
    letter-spacing: 0.24px;
    color: var(--text-dark, #161616);
}

.container-img {
    display: flex;
    justify-content: center;
    align-items: center;
    margin-top: 12px;
    width: 100%;
    height: 240px;
    background-color: #ffff;
    border-radius: 12px;
}

/*--------------@media запросы*/

/*--------------1280px--------*/
@media (max-width: 1280px) {
    .container-img {
        margin-top: 16px;
        width: 100%;
        height: 180px;
    }
}

/*--------------1024px--------*/
@media (max-width: 1024px) {
}

/*--------------768px--------*/
@media (max-width: 768px) {
    .container-img {
        margin-top: 12px;
        height: auto;
    }

    .item-title {
    font-size: 18px;
    line-height: 24px;
}
}

</style>