<script>
export default {
    data() {
        return {
        }
    },
    name: 'ClientLogo',
    components: {
    }
}
</script>

<template>
    <div class="ClientLogo">
        <div class="container-img">
            <slot></slot>
        </div>
    </div>
</template>

<style scoped>
.ClientLogo {
    border-radius: 16px;
    background: var(--back-hover, #F4F5F8);
}
.container-img {
    height: 100%;
    width: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
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
    .ClientLogo {
        border-radius: 12px;
    }
}
</style>