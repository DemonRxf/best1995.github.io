<template>
  <div class="content">
      <div class="column" v-for="(item,index) in list" :key="index">
          <span class="title"><Icon class="icon" :type="item.icon" />{{ item.name }}</span>
          <ul class="list">
              <li v-for="(it,i) in item.list" :key="i" @click="loadFun(it.url)">
                  <div class="tag" v-if="it.tag">{{ it.tag }}</div>
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
        padding: 10px 0 20px;
        background: #F7F8FA;
        .column{
            margin-top: 20px;
            padding: 20px 4px;
            background: #fff;
            .title{
                display: block;
                font-size: 16px;
                font-weight: 500;
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
                    position: relative;
                    width: 2.9rem;
                    min-height: 2.3rem;
                    flex-shrink: 0;
                    background: #f4f4f4;
                    margin-left: .15rem;
                    margin-bottom: .15rem;
                    display: flex;
                    flex-direction: column;
                    border-radius: 12px;
                    padding: 15px;
                    box-sizing: border-box;
                    .tag{
                        font-size: 12px;
                        position: absolute;
                        right: -5px;
                        top: -3px;
                        transform: scale(0.7);
                        background: #FC5531;
                        color: #fff;
                        padding: 3px 4px;
                        line-height: 1;
                        box-sizing: border-box;
                        border-radius: 0 12px 0 12px;
                    }
                    .list-top{
                        display: flex;
                        flex-direction: row;
                        align-items: center;
                        .list-logo{
                            width: 30px;
                            height: 30px;
                            margin-right: 5px;
                            border-radius: 50%;
                            box-shadow: 0 0 5px rgba(152,152,152,0.2);
                            background-size: contain;
                            background-repeat: no-repeat;
                            background-color: #f7f7f7;
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
                        text-align: justify;
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