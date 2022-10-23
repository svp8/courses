<template>
    <div class="card">
        <div class="card__bottom">
            <div class="card__bottom__main">
                <div class="caption">
                    <span>Название серии</span>
                </div>
                <h5>Базовые навыки профессиональных телефонных звонков</h5>
                <h5>21 000 ₽</h5>
            </div>
            <button class="about">
                Подробнее
                <img src="../assets/Vector60.png"/>
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
    width: 368.67px;
    height: 400px;
    position :relative;
    border-radius: 4px;
    background: url(../assets/photo.png);
    background-size: cover;
    background-position: top;
    border-radius: 4px;
    padding: 0px;
    &__bottom {
        display: flex;
        position: absolute;
        bottom: 0px;
        flex-direction: column;
        justify-content: flex-end;
        align-items: flex-start;
        padding: 0px 30px 25px 30px;
        gap: 12px;
        height:199px;
        // border: 1px solid black;
        // overflow: hidden;
        background: linear-gradient(0deg, #4C5A79 0%, rgba(76, 90, 121, 0) 100%);
        text-align: left;
        transition: height 300ms ease-out, background 300ms linear;
        border-radius: 4px;
        &__main {
            
            display: flex;
            flex-direction: column;
            justify-content: flex-end;
            align-items: flex-start;
            gap: 12px;
            text-align: left;
             transition: margin-bottom 300ms ease-out ;

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
        }

        .about {
            font-family: Houschka Pro;
            position:absolute;
            font-weight: 700;
            font-size: 18px;
            line-height: 28px;
            /* identical to box height, or 156% */
            background-color: transparent;
            border: 0;
            /* white */
            transform: translateY(50px);
            color: #FFFFFF;
            transition: transform 300ms ease-in;
            // visibility: hidden;
        }

    }


}

.card:hover .card__bottom {
    height:94%;
    padding-top: 0;
    background: linear-gradient(0deg, #4C5A79 0%, rgba(76, 90, 121, 0.75) 100%);
}
.card:hover .about{
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