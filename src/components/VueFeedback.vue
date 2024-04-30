<script>
import axios from 'axios'

export default {
    data() {
        return {
            feedback: {
                name: '',
                tel: '',
                email: '',
            },
        }
    },
    name: 'VueFeedback',
    components: {
    },
    methods: {
        submit() {
            this.feedback.name = ''
            this.feedback.tel = ''
            this.feedback.email = ''
            axios.post('/api/asdasd')
        },
    },
}
</script>

<template>
    <div class="VueFeedback">
        <!--------------Feedback-->
        <div class="flex-container">
            <div class="flex-item _info">
                <h1 class="title">Будем рады ответить на все интересующие вопросы</h1>
                <div class="subtitle">Оставьте заявку и мы вам вскоре позвоним и проконсультируем по всем интересующим
                    вопросам</div>
            </div>

            <div class="flex-item">
                <!-- Форма -->
                <form @submit.prevent.stop="submit()" class="form" action="#" id="form" method="post">
                    <div class="data">
                        <input class="form-data _text" type="text" v-model="feedback.name" placeholder="Ваше имя" required>

                        <input class="form-data _tel" type="tel" v-model="feedback.tel"
                            pattern="^\+7 \(\d{3}\) \d{3} \d{2} \d{2}$" placeholder="+ 7 (___) __ __" required>

                        <input class="form-data _email" type="email" v-model="feedback.email"
                            placeholder="E-mail (необязательно)" pattern="[a-z0-9._%+\-]+@[a-z0-9.\-]+\.[a-z]{2,}$">
                    </div>
                    <input class="form-submit" type="submit" value="Отправить">
                </form>
            </div>
        </div>
    </div>
</template>

<style scoped>
.VueFeedback {
    width: 100%;
    margin: 120px 0px;
}

.flex-container {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
    max-width: 1200px;
    padding: 60px 40px;
    border-radius: 20px;
    background: var(--back-button, #202226);
    gap: 16px;
}

.flex-item {
    display: flex;
    flex-direction: column;
    gap: 20px;
    min-width: 46%;
}

._info {
    width: 451px;
}

.title {
    margin: 0px;
    color: var(--text-light, #FFF);
    font-size: 40px;
    line-height: 48px;
}

.subtitle {
    color: var(---text-active, #9F9F9F);
    font-size: 16px;
    line-height: 20px;
}

.data {
    margin-bottom: 44px;
    display: flex;
    flex-direction: column;
    gap: 20px;
}

.form-data {
    height: 52px;
    align-items: center;
    color: var(---text-active, #9F9F9F);
    font-size: 16px;
    line-height: 20px;
    margin: 0px;
    padding: 0px;

    border: none;
    box-sizing: border-box;
    background: var(--back-button, #202226);
    outline: none;
    border-bottom: 2px solid var(--text-light, #fff);

}

.form-submit {
    align-items: end;
    text-align: start;
    padding: 12px 20px;
    background: var(--text-light, #FFF);
    border: none;
    border-radius: 8px;

    &:hover {
        background-color: var(--dived-hover);
        transition-duration: 0.3s;
    }
    &:active {
        background-color: var(--back-hover);
    }
}

/*--------------@media запросы*/

/*--------------1024px--------*/
@media (max-width: 1024px) {
    .flex-item {
        width: 100%;
    }
}

/*--------------900px--------*/
@media (max-width: 900px) {
    .VueFeedback {
        width: 100%;
        margin: 100px 0px;
    }

    .flex-container {
        padding: 36px;
        gap: 40px;
    }


}

/*--------------660px--------*/
@media (max-width: 660px) {
    .VueFeedback {
        width: 100%;
        margin: 60px 0px;
    }
}

/*--------------540px--------*/
@media (max-width: 540px) {
    .title {
        font-size: 24px;
        line-height: 28px;
    }

    .subtitle {
        font-size: 14px;
        line-height: 16px;
    }

    .form-data {
        font-size: 14px;
        line-height: 16px;
    }

    .form-submit {
        font-size: 14px;
        line-height: 16px;
    }


}

/*--------------355px--------*/
@media (max-width: 355px) {
    .flex-container {
        border-radius: 12px;
        padding: 12px;
        gap: 32px;
    }

    ._info {
        gap: 12px;
    }

    .data {
        gap: 8px;
        margin-bottom: 32px;
    }
}
</style>