<script>

export default {
    name: 'BasketCard',
    components: {
    },
    props: {
        title: String,
    },
}
</script>

<template>
    <div class="card-item">
        <div class="container-img">
            <slot></slot>
        </div>
        <div class="card-title">{{ title }}</div>
    </div>
</template>

<style scoped>
.container-img {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 100%;
    height: 160px;
    background-color: inherit;

   
}

.card-item {
    padding: 16px;
    box-sizing: border-box;
    border: 1px solid var(--dived-hover);
    display: flex;
    flex-direction: column;
    row-gap: 16px;

    &:hover {
        background-color: var(--dived-hover);
        transition-duration: 0.3s;
        border: 1px solid #000;
    }
    &:active {
        background-color: var(--back-hover);
    }
}

.card-title {
    text-align: center;
    font-weight: 500;
    font-size: 16px;
    line-height: 20px;
}

/*-----------------------------Media---------------------*/
@media (max-width: 1280px) {}

@media (max-width: 1024px) {
    .container-img {
        height: 100px;
    }
}

@media (max-width: 768px) {
    .card-item {
        row-gap: 10px;
    }
}
</style>
