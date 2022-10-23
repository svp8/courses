<template>
  <div class="main">
    <img style="align-self: flex-start" src="./assets/logoND.png" />
    <h1 class="title">Каталог курсов</h1>
    <SearchBar :info="data" @filter="filterData" />
    <div>
      <div class="middle">
        <span style="color:#4C5A79" class="caption">{{dataFiltered.length}} результатов</span>
        <ul class="middle__right">
          <li><span style="color:#9DB0BF" class="caption">Сортировать по:</span></li>
          <li class="sort">
            <span @click="sort(0)" :class="{'sort__name-active':sortParams[0].active}"
              class="sort__name caption">Цене</span>
            <img v-if="sortParams[0].active" :class="{'sort__img-up':sortParams[0].direction}"
              src="./assets/arrow-up.png" />
          </li>
          <li>
            <span @click="sort(1)" :class="{'sort__name-active':sortParams[1].active}"
              class="sort__name caption">Алфавиту</span>
            <img v-if="sortParams[1].active" :class="{'sort__img-up':sortParams[1].direction}"
              src="./assets/arrow-up.png" />
          </li>
        </ul>
      </div>
      <div class="cards">
        <Card v-for="card in dataFiltered" :key="card.id" :info="card" />
      </div>
    </div>
    <button @click="changePage(2)">
      next
    </button>


  </div>

</template>

<script>
import Card from '@/components/Card.vue'
import SearchBar from '@/components/SearchBar.vue';

import { mock } from '@/assets/api/mock'
import { onBeforeMount, ref, computed } from 'vue'


export default {
  name: 'App',
  components: {
    Card,
    SearchBar
  },
  setup() {

    onBeforeMount(() => {
      currentPage.value = 1;
      currentPageSize.value = 9;
      data.value = mock;
      dataFiltered.value = data.value;
      page.value = mock.slice((currentPage.value - 1) * currentPageSize.value, currentPage.value * currentPageSize.value);
    })
    const data = ref([]);
    const dataFiltered = ref([]);
    const page = ref([]);
    const sortParams = ref([{ active: false, direction: true }, { active: false, direction: true }]);
    const currentPage = ref(null);
    const currentPageSize = ref(null);
    const changePage = (next) => {
      currentPage.value = next;
      page.value = data.slice((currentPage.value - 1) * currentPageSize.value, currentPage.value * currentPageSize.value)
    }
    const filterData = (filter) => {
      update(filter);
    }
    const update = (value) => {
      dataFiltered.value = value;
      currentPage.value = 1;
      currentPageSize.value = 9;
      sortParams.value.map((item, index) => {
        if (item.active === true) {
          sortByParam(index, item.direction);
        }
      })
      page.value = value.slice((currentPage.value - 1) * currentPageSize.value, currentPage.value * currentPageSize.value);
    }
    const sort = (num) => {
      switch (num) {
        case 0:
          sortParams.value[0].active = true;
          sortParams.value[1].active = false;
          sortParams.value[num].direction = !sortParams.value[num].direction;
          sortByParam(0, sortParams.value[num].direction);
          break;
        case 1:
          sortParams.value[0].active = false;
          sortParams.value[1].active = true;
          sortParams.value[num].direction = !sortParams.value[num].direction;
          sortByParam(1, sortParams.value[num].direction);
          break;
        default:
          break;
      }
    }
    const sortByParam = (num, direction) => {
      switch (num) {
        case 0:
          if (direction) {
            dataFiltered.value.sort((a, b) => a.cost - b.cost);
          }
          else dataFiltered.value.sort((a, b) => b.cost - a.cost)
          break;
        case 1:
        if (direction) {
          dataFiltered.value.sort((a, b) => {
            let fa = a.title.toLowerCase(),
              fb = b.title.toLowerCase();

            if (fa < fb) {
              return -1;
            }
            if (fa > fb) {
              return 1;
            }
            return 0;
          })
          }
          else 
          dataFiltered.value.sort((a, b) => {
            let fa = a.title.toLowerCase(),
              fb = b.title.toLowerCase();

            if (fa < fb) {
              return 1;
            }
            if (fa > fb) {
              return -1;
            }
            return 0;
          })
          break;
        default:
          break;
      }
    }

    return {
      page: computed(() => data.value.slice((currentPage.value - 1) * currentPageSize.value, currentPage.value * currentPageSize.value)),
      currentPage,
      currentPageSize,
      changePage,
      filterData,
      data,
      dataFiltered,
      sortParams,
      sort
    }
  }
}
</script>

<style lang="scss">
* {
  padding: 0;
  margin: 0;
  list-style: none;
}

#app {
  font-family: 'Houschka Pro';
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;

}

html {
  width: 100%
}

.caption {
  font-weight: 500;
  font-size: 15px;
  line-height: 19px;
}

.main {
  padding: 30px 100px;
  display: flex;
  flex-direction: column;
  text-align: start;
  padding: 30px 100px 60px;
  gap: 30px;

  .title {
    color: #4C5A79;
    font-size: 42px;
    line-height: 50px;
  }

  .middle {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    margin-bottom: 15px;

    &__right {
      li {
        display: inline;
        margin-right: 15px;
        cursor: pointer;
        user-select: none;

        .sort__name {
          color: #0066B3;
          border-bottom: 1px #0066B3 dashed;

          &-active {
            border-bottom: 0;
            color: #4C5A79;
          }

          &:hover {
            color: #EB3737;
            border-bottom: 1px #EB3737 dashed;
          }

          &:active {
            color: #C52020;
            border-bottom: 0;
          }
        }

        .sort__img-up {
          transform: rotate(-180deg);
        }
      }
    }
  }

  .cards {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    gap: 30px;
  }

  @media (max-width: 1100px) {
    .cards {
      grid-template-columns: 1fr 1fr;
    }
  }
}
</style>
