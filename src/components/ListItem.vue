<template>
  <div class="news-view">
      <ul class="news-view__list">
        <li v-for="(item,i) in list" :key="i" class="news-view__post">
          
          <div class="news-view__points">
            {{item.points || 0}}
          </div>

          <div>
            <p class="news-view__title">
              <template v-if="item.domain">
                <a :href="item.url">{{item.title}}</a>
              </template>
              <template v-else>
                <router-link :to="`item/${item.id}`">
                  {{item.title}}
                </router-link>
              </template>
            </p>
             <small class="news-view__link" v-if="item.user">
              {{item.time_ago}} by <router-link :to="`/user/${item.user}`" class="news-view__link"> {{item.user}}</router-link>
            </small>
            <small class="news-view__link" v-else>{{item.time_ago}}, {{item.domain}}</small>
 
          </div>
        </li>
      </ul>
    </div>
</template>

<script>
import { mapState} from 'vuex';
export default {
//  props:{
//     list: {
//       type: Array,
//       default: () => [],
//     },
//   },
  computed:{
    ...mapState(['list']),

  },
}
</script>

<style lang="scss" scoped>
.news-view{
  &__list{
    margin: 0;
    padding: 0;
  }
  &__post{
    list-style: none;
    display: flex;
    align-items: center;
    border-bottom: 1px solid #eee;
  }
  &__points{
    width: 80px;
    height: 60px;
    display: flex;
    align-items: center;
    justify-content: center;
    color: #42b882;
  }
  &__title{
    margin: 0;
  }
  &__link{
    color: #828282;
  }
}
</style>