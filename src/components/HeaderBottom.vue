<script>
import Logo from './Logo.vue'

export default {
    data() {
        return {
            active: false,
        }
    },
    methods: {
        classSwitch() {
            this.active = !this.active
            const body = document.body
            body.classList.toggle('active')
        },
        classOff() {
            this.active = false
            const body = document.body
            body.classList.remove('active')
        },
    },
    name: 'HeaderBottom',
    components: {
        Logo,
    },
}
</script>
    
<template>
    <div class="HeaderBottom">
        <div class="grid-wrapper" :class="{ _active: active }">

            <div class="links" :class="{ _active: active }">
                <div @click="classOff()" class="logo-burger" :class="{ _active: active }">
                    <Logo />
                </div>
                <router-link @click="classOff()" to="/catalog" class="links-item">Каталог</router-link>
                <a href="#" @click="classOff()" class="links-item">Наше производство</a>
                <router-link @click="classOff()" to="/AboutCompany" class="links-item">О компании</router-link>
                <router-link @click="classOff()" to="/Contacts" class="links-item">Контакты</router-link>
                <router-link @click="classOff()" to="/Payment" class="header__functions-item">Доставка и
                    оплата</router-link>
                <router-link @click="classOff()" to="/Guarantee" class="header__functions-item">Гарантия</router-link>
                <div class="container-request"></div>
                <a href="#" @click="classOff()" class="request-burger">Запросить консультацию</a>
            </div>

            <div class="icon">
                <router-link to="/Basket" class="header__icon-link">
                    <img src="../assets/header/Cart.png" alt="" class="header__icon-item" />
                </router-link>
            </div>

            <div @click="classSwitch()" :class="{ _active: active }" class="burger">
                <div class="burger-cross"></div>
            </div>

            <a href="#" class="request">Запросить консультацию</a>
        </div>
    </div>
</template>
  
  
<style scoped>
.HeaderBottom {
    max-width: 100%;
    padding: 28px 0px 32px 0px;
    background: #fff;
}

.logo-burger {
    display: none;
}

.grid-wrapper {
    display: grid;
    column-gap: 8px;
    grid-template-columns: 1fr auto auto;
    grid-template-areas:
        "links icon btn"
    ;
}

.header__functions-item {
    display: none;

    padding: 12px 20px;

    font-weight: 400;
    font-size: 16px;
    line-height: 20px;
    color: var(--text-dark);
    border-radius: 5px;
    background: var(--back-hover);
}

.links {
    grid-area: links;
    flex: 1 1 auto;
    display: flex;
    gap: 8px;
}

.request-burger {
    display: none;
}

.links-item {
    padding: 12px 20px;

    font-weight: 400;
    font-size: 16px;
    line-height: 20px;
    color: var(--text-dark);
    border-radius: 5px;
    background: var(--back-hover);

    &:hover {
        background-color: var(--dived-hover);
        transition-duration: 0.3s;
    }
    &:active {
        background-color: var(--back-hover);
    }
}

.icon {
    grid-area: icon;
    display: flex;
    gap: 8px;
}

.header__icon-link {
    height: 20px;
    width: 20px;
    padding: 10px;

    border-radius: 8px;
    background: var(--back-hover);

    &:hover {
        background-color: var(--dived-hover);
        transition-duration: 0.3s;
    }
    &:active {
        background-color: var(--back-hover);
    }
}

.header__icon-item {
    width: 22px;
    height: 22px;
    display: inline-block;
    text-align: center;
}

.request {
    max-width: 200px;
    grid-area: btn;
    display: inline-block;
    padding: 12px 20px;

    font-weight: 400;
    font-size: 16px;
    line-height: 20px;
    background: var(--back-button);
    border-radius: 8px;
    color: var(--text-light);
}


/*-----------------------------Media---------------------*/


@media (max-width: 1280px) {
    .icon {
        justify-content: end;
    }

    .grid-wrapper {
        row-gap: 8px;
        grid-template-columns: auto 1fr;
        grid-template-areas:
            "links icon"
            "btn btn"
        ;
    }
}

@media (max-width: 1024px) {
    .icon {
        justify-content: start;
    }

    .grid-wrapper {
        row-gap: 8px;
        grid-template-columns: auto 1fr;
        grid-template-areas:
            "links links"
            "icon btn"
        ;
    }

    .links {
        width: 100%;
        justify-content: space-between;
    }

    .links-item {
        font-size: 16px;
    }
}

@media (max-width: 768px) {
    .grid-wrapper._active {
        position: absolute;
        top: -56px;
        right: 16px;
    }

    .logo-burger._active {
        padding: 24px 16px;
        position: fixed;
        top: 0px;
        left: 0px;
        display: inline-block;
        width: 100%;
        margin-bottom: 28px;
        background-color: var(--back-hover);
    }

    .grid-wrapper {
        gap: 0px;
        grid-template-columns: 1fr auto;
        grid-template-areas:
            "icon burger"
        ;
    }

    .links {
        left: -100%;
        overflow: auto;
        transition: left 0.3s ease 0s;

        justify-content: flex-start;
        padding: 80px 16px 24px 16px;
        background-color: #fff;
        position: fixed;
        top: 0;
        box-sizing: border-box;
        height: 100%;
        grid-area: none;
        flex: none;
        width: 100%;
        max-width: 100%;
        display: flex;
        flex-direction: column;
        gap: 0px;
        z-index: 10;
    }

    .links._active {
        left: 0px;
    }

    .links-item {
        font-size: 14px;
        font-style: normal;
        font-weight: 400;
        line-height: 16px;

        background-color: #fff;
        border-bottom: solid 1px var(--dived-hover);
        padding: 16px 0px;
    }

    .request-burger {
        display: inline-block;

        margin-top: 20px;
        text-align: center;
        padding: 14px 20px;
        font-weight: 400;
        font-size: 16px;
        line-height: 20px;
        background: var(--back-button);
        border-radius: 8px;
        color: var(--text-light);
    }

    .container-request {
        display: flex;
        flex: 1 0 auto;
    }

    .header__functions-item {
        display: inline-block;
        background-color: #fff;
        border-bottom: solid 1px var(--dived-hover);
        padding: 16px 0px;
    }

    .request {
        display: none;
    }

    .burger {
        z-index: 10;
        grid-area: burger;
        position: relative;
        border-radius: 8px;
        background: var(--back-hover);
    }

    .burger._active {
        right: 16px;
        top: 16px;
        position: fixed;
        z-index: 100;
        background-color: #fff;
    }

    .burger-cross {
        z-index: 20;
        margin: 19px 11px;
        width: 18px;
        height: 2px;
        background: var(--text-dark);
    }

    .burger-cross::before {
        position: absolute;
        background: var(--text-dark);
        width: 18px;
        height: 2px;
        content: "";
        top: 14px;
        left: calc(50% - 9px);
    }

    .burger-cross::after {
        position: absolute;
        background: var(--text-dark);
        width: 18px;
        height: 2px;
        content: "";
        bottom: 14px;
        left: calc(50% - 9px);
    }
}
</style>