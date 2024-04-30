<script>
import axios from 'axios'

export default {
    data() {
        return {
            feedback: {
                name: '',
                tel: '',
                pasportId: '',
                address: '',
            },
        }
    },
    name: 'ContactDetails',
    components: {
    },
    methods: {
        submit() {
            this.feedback.name = ''
            this.feedback.tel = ''
            this.feedback.address = ''
            this.feedback.pasportId = ''
            axios.post('/api/asdasd')
            alert('asd')
        },
    },
}
</script>

<template>
    <form @submit.prevent.stop="submit()" class="VueFeedback" id="form" method="post">
        <!--------------Feedback-->
        <div class="form-container">
            <div class="title">Контактные данные</div>

            <!-- Форма -->
            <div class="form" action="#">
                <div class="data">
                    <input class="form-data _text" type="text" v-model="feedback.name" placeholder="ФИО" required>
                    <input class="form-data _text" type="text" v-model="feedback.address" placeholder="Адрес" required>

                    <input class="form-data _tel" type="tel" v-model="feedback.tel"
                        pattern="^\+7 \(\d{3}\) \d{3} \d{2} \d{2}$" placeholder="+ 7 (___) __ __" required>

                    <input class="form-data _text" type="text" v-model="feedback.pasportId" placeholder="Номер паспорта"
                        required>
                </div>

            </div>

        </div>
        <input class="form-submit" type="submit" value="Отправить">
    </form>
</template>

<style scoped>
.VueFeedback {
    width: 100%;
    margin: 120px 0px;
}

.form-container {
    padding: 60px 40px;
    border-radius: 20px;
    background: var(--back-button, #202226);
    gap: 16px;
}

.title {
    margin-bottom: 40px;
    color: var(--text-light, #FFF);
    font-size: 24px;
    line-height: 28px;
}

.data {
    display: grid;
    grid-template-columns: repeat(2, minmax(280px, 1fr));
    width: 100%;
    margin-bottom: 44px;
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
    margin-top: 20px;
    color: #FFF;
    align-items: end;
    text-align: start;
    padding: 12px 20px;
    background: var(--back-button, #000);
    border: none;
    border-radius: 8px;
}

/*--------------@media запросы*/

/*--------------1280px--------*/
@media (max-width: 1280px) {
    .VueFeedback {
        width: 100%;
        margin: 100px 0px;
    }

    .form-container {
        padding: 36px;
        gap: 40px;
    }
}

/*--------------768px--------*/
@media (max-width: 768px) {
    .VueFeedback {
        width: 100%;
        margin: 60px 0px;
    }

    .form-container {
        border-radius: 12px;
        padding: 12px;
        gap: 32px;
    }

    .data {
        grid-template-columns: repeat(1, minmax(200px, 1fr));
        gap: 8px;
        margin-bottom: 32px;
    }

    .title {
        font-size: 24px;
        line-height: 28px;
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
</style>