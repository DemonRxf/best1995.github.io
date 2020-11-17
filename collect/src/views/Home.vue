<template>
  <div class="content">
      <div class="column" v-for="(item,index) in list" :key="index">
          <span class="title"><Icon class="icon" type="ios-school-outline" />{{ item.name }}</span>
          <ul class="list">
              <li v-for="(it,i) in item.list" :key="i" @click="loadFun(it.url)">
                  <div class="list-top">
                      <div class="list-logo"  :style="{backgroundImage:'url('+it.img+')'}"></div>
                      <span class="list-title">{{ it.title }}</span>
                  </div>
                  <div class="list-content">
                      {{ it.describe }}
                  </div>
              </li>
          </ul>
      </div>
      <BackTop :bottom="100" :right="10"></BackTop>
  </div>
</template>

<script>
    import axios from 'axios'
export default {
  name: 'Home',
  data(){
      return{
          list:[]
      }
  },
    mounted() {
        axios.get('./collect.json').then(res =>{
            const { data } = res.data;
            this.list = data;
        })
    },
    methods:{
        loadFun(res){
            window.open(res)
        }
    }
}
</script>

<style lang="scss">
    .content{
        padding: 20px 10px;
        .column{
            margin-bottom: 30px;
            .title{
                display: block;
                font-size: 18px;
                color: #333;
                margin: 0 10px 20px;
                .icon{
                    margin-right: 10px;
                }
            }
            .list{
                display: flex;
                flex-direction: row;
                flex-wrap: wrap;
                li{
                    width: 180px;
                    height: 130px;
                    background: #f9f9f9;
                    margin-left: 10px;
                    margin-bottom: 10px;
                    display: flex;
                    flex-direction: column;
                    border-radius: 10px;
                    padding: 15px;
                    box-sizing: border-box;
                    .list-top{
                        display: flex;
                        flex-direction: row;
                        align-items: center;
                        .list-logo{
                            width: 30px;
                            height: 30px;
                            margin-right: 5px;
                            border-radius: 50%;
                            box-shadow: 0 0 5px rgba(0,0,0,0.1);
                            background-size: cover;
                            background-repeat: no-repeat;
                            background-color: #fefefe;
                            background-position: center;
                        }
                        .list-title{
                            font-weight: 600;
                        }
                    }
                    .list-content{
                        overflow: hidden;
                        text-overflow: ellipsis;
                        display: -webkit-box;
                        -webkit-line-clamp: 3;
                        -webkit-box-orient: vertical;
                        margin-top: 10px;
                    }
                }
            }
        }
    }
    ul,li{
        margin: 0;
        padding: 0;
        list-style: none;
    }
</style>