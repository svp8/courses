<template>
    <div class="card">
        <div class="card__bottom">
            <div>
                <div class="caption">
                    <span>Название серии</span>
                </div>
                <h5>Базовые навыки профессиональных телефонных звонков</h5>
                <h5>21 000 ₽</h5>
            </div>

            <button class="about">
                Подробнее
            </button>
        </div>
    </div>

</template>
<style lang="scss">
.anim {
    transition: 0.5s;
    transform: translateY(100%);
    height: 100px;
}

.card:hover .anim {
    transform: translateY(0);
    height: 100px;
}

.card {
    width: 272px;
    height: 400px;
    border-radius: 4px;
    background: url(../assets/photo.png);
    background-size: cover;
    background-position: top;
    border-radius: 4px;
    display: flex;
    flex-direction: column;
    justify-content: flex-end;
    align-items: flex-start;
    padding: 0px;
    gap: 12px;

    &__bottom {
        display: flex;
        flex-direction: column;
        justify-content: flex-end;
        align-items: flex-start;
        padding: 56px 30px 25px;
        gap: 12px;
        // border: 1px solid black;
        // width: 272px;
        flex: 0;
        background: linear-gradient(0deg, #4C5A79 0%, rgba(76, 90, 121, 0) 100%);
        text-align: left;
        transition: flex 300ms ease-out, background-color 300ms ease-out;

        .caption {
            display: flex;
            align-items: center;
            padding: 2px 10px 0px;
            font-weight: 500;
            font-size: 15px;
            line-height: 19px;
            color: #FFFFFF;
            background-color: #0066B3;
            border-radius: 2px;
        }

        h5 {
            font-style: normal;
            font-weight: 800;
            font-size: 18px;
            line-height: 25px;
            text-transform: uppercase;
            color: #FFFFFF;


        }

        .about {
            font-family: Houschka Pro;
            font-weight: 700;
            font-size: 18px;
            line-height: 28px;
            /* identical to box height, or 156% */
            background-color: transparent;
            border: 0;
            visibility: collapse;
            /* white */

            color: #FFFFFF;
        }

    }


}

.card:hover .card__bottom {
    flex: 1;
    background: linear-gradient(0deg, #4C5A79 0%, rgba(76, 90, 121, 0.75) 100%);
}

.card:hover .card__bottom {
    flex: 1;
    background: linear-gradient(0deg, #4C5A79 0%, rgba(76, 90, 121, 0.75) 100%);
}

.card:active {
    box-shadow: inset 0px 5px 10px rgba(0, 0, 0, 0.4);
}
</style>