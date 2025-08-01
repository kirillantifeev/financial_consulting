<template>
                <div style="display: flex;">
                    <div style="margin-right: 16px;">
                        <slot></slot>
                    </div>
                    
                    <div>
                        <div class="info-title">
                            <slot name="title"></slot>
                        </div>
                        <div class="info-text">
                            <slot name="text" ></slot>
                        </div>
                    </div>  
                </div>
</template>

<script setup>

</script>

<style scoped>
    .info-title {
        font-family: 'Lato', sans-serif;
        font-weight: 400;
        font-size: 16px;
        color: var(--additional-text);
    }

    .info-text {
        font-family: 'Cabin', sans-serif;
        font-weight: 600;
        font-size: 20px;
        color: var(--main-text);
    }

    @media (max-width: 500px) {
        .info-text {
            font-size: 16px;
        }    
    }
</style>