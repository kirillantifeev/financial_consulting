<template>
    <div class="container__contacts">
        <div class="block__contact">
            <div>
                <UiButtonProccess>Proccess</UiButtonProccess>
                <h4 class="contact-title">Contact Us. It’s Easy.</h4>
                <p class="contact-text">
                    Leverage agile frameworks to provide a robust synopsis for high level overviews. 
                    Iterative approaches to corporate strategy foster collaborative.
                </p>
            </div>
            <div class="block__info">
                <InfoPoint>
                    <SvgCall/>
                    <template #title>Call Today</template>
                    <template #text>+1 800 100 900</template>
                </InfoPoint>
                <InfoPoint>
                    <SvgTime/>
                    <template #title>Monday To Friday</template>
                    <template #text>9AM - 5PM</template>
                </InfoPoint>
                <InfoPoint>
                    <SvgAddress/>
                    <template #title>USA Office</template>
                    <template #text>195 Devonshire St Boston, MA 02110</template>
                </InfoPoint>
            </div>
        </div>
        <div class="block-form">
            <ContactForm/>
        </div>
    </div>
</template>

<script setup>
import UiButtonProccess from './UI/UiButtonProccess.vue';
import SvgCall from '@/assets/Svg/SvgCall.vue';
import InfoPoint from './InfoPoint.vue';
import SvgTime from '@/assets/Svg/SvgTime.vue';
import SvgAddress from '@/assets/Svg/SvgAddress.vue';
import ContactForm from './ContactForm.vue';

</script>

<style scoped>
    .container__contacts {
        width: 100%;
        display: flex;
        margin-top: 111.9px;
        gap: 91px;
        margin-bottom: 136px;
    }

    .block__contact {
        width: 35%;
        display: flex;
        flex-direction: column;
        gap: 38px;
    }

    .block-form {
        flex-grow: 1;
    }

    .contact-title {
        font-family: 'Cabin', sans-serif;
        font-weight: 700;
        font-size: 45px;
        color: var(--main-text);
        margin-top: 6px;
    }
    
    .contact-text {
        font-family: 'Lato', sans-serif;
        font-weight: 400;
        font-size: 16px;
        color: var(--additional-text);
        margin-top: 13px;
    }

    .block__info {
        display: flex;
        flex-direction: column;
        gap: 56px;
    }

    @media(max-width: 1300px) {
    .container__contacts {
        margin-bottom: 106px;
    }

    }


    @media (max-width: 1050px) {
        .container__contacts {
            flex-direction: column;
            margin-top: 50px;
        }

        .block__contact {
            width: 100%;
            
        }
    }

    @media (max-width: 900px) {

    .container__contacts {
        margin-bottom: 86px;
    }

    .contact-title {
        font-size: 35px;
    }
    }

    @media (max-width: 470px) {
        .contact-title {
            font-size: 29px;
    }
    }
</style>