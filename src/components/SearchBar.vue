<template>
    <div class="search-bar">
        <input />
        <div class="search-bar-icon">
            <img style="position: absolute;
width: 13px;
height: 13px;
left: 7px;
top: 4px;" src="../assets/Ellipse13.png" />
            <img style="position: absolute;

left:5px;
top: 14px;
" src="../assets/Line13.png" />
        </div>

    </div>
</template>
<style lang="scss" scoped>
.search-bar {
    display: flex;
    background: #F0F4FC;
    border-radius: 4px;
    height: 58px;
    position: relative;

    &-icon {
        position: absolute;
        right: 40px;
        top: 21px
    }

    input {
        background: inherit;
        border: 0;
        height: inherit;
        flex: 1;
        border-radius: inherit;
        transition: background 300ms ease-out;

        &:hover {
            background: #E2E8F3;
        }

    }
}
</style>