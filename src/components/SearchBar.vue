<template>
    <div class="search-bar">
        <div style="flex:1;display:flex">
            <input v-on:keyup.enter="onEnter" v-model="searchText" type="text" name="text" class="text" required />

            <label for="text" class="text search-bar__label ">
                <span class="content-name">
                    Поиск по каталогу
                </span>
            </label>
        </div>
        <div @click="onEnter" style="width:50px;cursor: pointer;z-index: 10;">
        </div>
        <!-- building search icon -->
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

<script>
import { ref, onBeforeMount } from 'vue'
export default {
    props: ['info'],
    emits: ['filter'],
    setup(props, { emit }) {
        onBeforeMount(() => {
            searchText.value = localStorage.getItem('searchText');
        })
        const searchText = ref('')
        const filteredData = ref([]);
        const onEnter = () => {
            filteredData.value = [];
            if (searchText.value != '') {
                props.info.map((item) => {
                    if (item.title.toLowerCase().indexOf(searchText.value.toLowerCase().trim()) > -1) {
                        filteredData.value.push(item);
                    }
                })
                //send to app filtered array
                emit('filter', filteredData.value);
            }
            else emit('filter', props.info);
            localStorage.setItem('searchText', searchText.value)

        }

        return {
            searchText,
            onEnter
        }
    }
}
</script>

<style lang="scss" scoped>
.search-bar {
    background: #F0F4FC;
    border-radius: 4px;
    position: relative;
    overflow: hidden;
    display: flex;
    flex-direction: row;

    &-icon {
        position: absolute;
        right: 40px;
        top: 18px
    }

    &:hover {
        background: #E2E8F3;
    }

    &:focus {
        background: #F0F4FC;
        border: 1px solid #F0F4FC;
        box-shadow: inset 0px 2px 2px rgba(0, 0, 0, 0.12);
        outline: none;
    }

    &:active {
        background: #F0F4FC;
        box-shadow: inset 0px 2px 2px rgba(0, 0, 0, 0.12);
        outline: none;
    }

    input {
        padding: 15px 20px;
        padding-right: 0;
        background: inherit;
        border: 0;
        flex: 1;
        border-radius: inherit;
        transition: background 300ms ease-out;
        border-radius: 4px;
        outline: none;

        &:active {

            outline: none;
        }

        &:focus+.search-bar__label,
        &:valid+.search-bar__label {
            width: 45px;
            height: 19px;
            left: 17px;
            overflow: hidden;
            top: 0px;
            padding-left: 5px;
            font-weight: 500;
            font-size: 13px;
            line-height: 16px;
            color: #4C5A79;
            background: #E2E8F3;
            border-radius: 0px 0px 2px 2px;
        }

    }

    &__label {
        position: absolute;
        pointer-events: none;
        top: 15px;
        left: 15px;
        color: #4C5A79;
        transition: all 0.3s ease-out;
    }
}
</style>