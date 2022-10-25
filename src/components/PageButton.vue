<template>
    <button class="page-button text-bold" :class="{ disabled: disabled, active: active }" :disabled="disabled">
        <span v-if="arrow == 0">{{ num }}</span>
        <img v-if="arrow !== 0" :class="{ left: arrow == 1, off: disabled }" src="../assets/Vector39.svg" />
    </button>
</template>
<script>
export default {
    props: {
        num: [Number,String],
        active: Boolean,
        arrow: {
            default: 0
        },
        disabled: {
            default: false
        }
    },
}
</script>
<style lang="scss" scoped>
.page-button {
    display: flex;
    cursor: pointer;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    padding: 0px;
    gap: 7px;
    width: 50px;
    height: 50px;
    background: #F0F4FC;
    color: #0066B3;
    border-radius: 3px;
    user-select: none;
    transition: background 300ms ease-out;
    border: 0;

    &:hover {
        background: #E2E8F3;
    }

    &:active {
        background: #E2E8F3;
        box-shadow: inset 0px 3px 4px rgba(0, 0, 0, 0.2);
    }
}

@media (max-width: 759px){
    .page-button{
        width: 40px;
        height:40px;
    }
} 
.active {
    background: #4C5A79;
    color: white;

    &:hover {
        background: #4C6A8a;
    }
}

.left {
    transform: rotate(180deg);

}

.disabled {
    background: #E2E8F3;
    color: #9DB0BF;
    cursor: default;
}

.off {
    filter: invert(93%) sepia(52%) saturate(6230%) hue-rotate(175deg) brightness(83%) contrast(77%);

}
</style>