<template>
  <div class="main">
    <img style="align-self: flex-start" src="./assets/logoND.png" />
    <h1 class="title">Каталог курсов</h1>
    <SearchBar/>
    <div>
      <div class="middle">
        <span style="color:#4C5A79" class="caption">результатов</span>
        <ul class="middle__right">
          <li><span style="color:#9DB0BF" class="caption">Сортировать по:</span></li>
          <li class="sort">
            <span class="sort__name caption">Цене</span>
            <img />
          </li>
          <li>
            <span class="sort__name caption">Алфавиту</span>
            <img />
          </li>
        </ul>
      </div>
      <div class="cards">
        <Card v-for="card in 9" :key="index" />
      </div>
    </div>



  </div>

</template>

<script>
import Card from '@/components/Card.vue'
import SearchBar from '@/components/SearchBar.vue';
export default {
  name: 'App',
  components: {
    Card,
    SearchBar
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

        .sort__name {
          color: #0066B3;
          border-bottom: 1px #0066B3 dashed;

          &:hover {
            color: #EB3737;
            border-bottom: 1px #EB3737 dashed;
          }

          &:active {
            color: #C52020;
            border-bottom: 0;
          }
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
