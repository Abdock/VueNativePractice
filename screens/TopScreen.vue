<template>
  <view class="container">
    <text class="heading">Top users</text>
    <scroll-view class="top-container">
        <flat-list
            :data="$data.json" >
            <view render-prop-fn="renderItem">
                <view :style="{backgroundColor: '#eee', marginBottom: 5, marginTop: 5,marginLeft: 5, marginRight: 5, borderRadius:15 , paddingLeft: 20,paddingTop:20, paddingBottom:20 , flex: 1, alignItems: 'center', flexDirection: 'row'}" >
                    <image :style="{width: 60, height: 60, borderRadius: 50}" :source="{uri: args.item.icon}" />
                        <view>
                            <text :style="{color: '#767', marginLeft: 20, fontSize: 18}">{{args.item.name}}</text>
                            <text :style="{color: '#282', marginLeft: 20, fontSize: 12}">{{args.item.pos}}</text>
                        </view>
                    <text :style="{color: 'green', flex: 1, textAlign: 'right', paddingRight: 20, fontSize: 24}">{{args.item.scores}}</text>
                </view>
            </view>
        </flat-list>
    </scroll-view>
  </view>
</template>

<style>
.container {
    align-items: center;
    justify-content: center;
    flex: 1;
}
.heading {
    font-size: 30px;
    font-weight: bold;
    color: darkolivegreen;
    margin: 20px;
}
.top-container
{
    width: 100%;
}
</style>

<script>
import data from './../data/db.json';
const ratings = ["Сын маминой подруги", "Как тебе такое Илон Маск?", "Хранитель природы", "Друид", "Глава природы", "Глава Green Peace", "Участник Green Peace", "Эко активист", "Топим за экологию", "Мама я в топе"];

export default {
    data()
    {
        const list = data.residents;
        const result = [];
        const len = ratings.length < list.length ? ratings.length : list.length;
        for(let i = 0; i < len; ++i)
        {
            result.push({name: list[i].fullName, icon: list[i].account.avatar, scores: list[i].account.scores, pos: ''});
        }
        result.sort((a, b)=>{return b.scores - a.scores});
        for(let i = 0; i < len; ++i)
        {
            result[i]['pos'] = ratings[i];
        }
        return {json: result};
    }, 
}
</script>