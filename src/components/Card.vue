<template>
    <div class="card" :style="image">
        <div class="card__bottom">
            <div class="card__bottom__main">
                <div class="caption">
                    <span>{{ info.series }}</span>
                </div>
                <h5>{{ info.title }}</h5>
                <h5>{{ cost + " " + info.cost_currency }}</h5>
            </div>
            <button class="about text-bold">
                Подробнее
                <img src="../assets/Vector60.png" />
            </button>
        </div>
    </div>

</template>

<script>
import { onBeforeMount, ref, computed } from 'vue'
export default {
    props: ['info'],
    setup(props) {
        const data = ref([]);
        let path = require('@/assets/' + props.info.preview_img_path);
        const image = {
            background: `url(${path})`,
            "background-size": "cover",
            "background-position": "top",
            "border-radius": "4px",
        };

        return {
            data,
            image,
            cost: computed(() => {
                return (props.info.cost + "").replace(/\B(?=(\d{3})+(?!\d))/g, " ")
            })
        }
    }
}
</script>

<style lang="scss">
.card {
    width: 100%;
    height: 400px;
    position: relative;
    border-radius: 4px;
    background: url(../assets/logo.png);
    background-size: cover;
    background-position: top;
    border-radius: 4px;
    padding: 0px;
    overflow: hidden;

    &__bottom {
        display: flex;
        position: absolute;
        bottom: 0px;
        flex-direction: column;
        justify-content: flex-end;
        align-items: flex-start;
        padding: 0px 30px 25px 30px;
        gap: 12px;
        height: 60%;
        max-width: 95%;
        min-width: 95%;
        background: linear-gradient(0deg, #4C5A79 0%, rgba(76, 90, 121, 0) 100%);
        text-align: left;
        transition: all 300ms ease-out;
        border-radius: 4px;

        &__main {

            display: flex;
            flex-direction: column;
            justify-content: flex-end;
            align-items: flex-start;
            gap: 12px;
            text-align: left;
            transition: margin-bottom 300ms ease-out;
            max-width: 80%;

            .caption {
                display: flex;
                align-items: center;
                padding: 2px 10px 0px;
                color: #FFFFFF;
                background-color: #0066B3;
                border-radius: 2px;
            }

            h5 {
                text-transform: uppercase;
                color: #FFFFFF;
            }
        }

        .about {
            position: absolute;
            background-color: transparent;
            border: 0;
            transform: translateY(50px);
            color: #FFFFFF;
            transition: transform 300ms ease-in;
        }

    }


}

.card:hover .card__bottom {
    height: 94%;
    padding-top: 0;
    background: linear-gradient(0deg, #4C5A79 0%, rgba(76, 90, 121, 0.75) 100%);
}

.card:hover .about {
    transform: translateY(10px);
    visibility: visible;
}

.card:hover .card__bottom__main {
    margin-bottom: 20px;

}

.card:active {
    box-shadow: inset 0px 5px 10px rgba(0, 0, 0, 0.4);
}
</style>