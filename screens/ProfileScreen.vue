<template>
    <view class="container">
        <text class="heading">Profile</text>
        <flat-list
            :data="$data.json" >
            <view render-prop-fn="renderItem">
                <image :style="{width: 300, height: 300, borderRadius: 300}" :source="{uri: args.item.info.account.avatar}" />
                <text :style='{flex: 1, textAlign: "center", fontSize: 28, color: "darkgreen", marginTop: 20}'>{{args.item.info.fullName}}</text>
                <view :style="{flex: 1, flexDirection: 'row', marginTop: 50}">
                    <view :style="{flex: 4, alignItems: 'center', paddingTop: 4, height: 30 + 200 * args.item.info.account.trashType.metal / args.item.info.account.scores, backgroundColor: 'red'}">
                        <text :style="{color: '#eee'}">Metal</text>
                    </view>
                    <view :style="{flex: 4, alignItems: 'center', paddingTop: 4, height: 30 + 200 * args.item.info.account.trashType.paper / args.item.info.account.scores, backgroundColor: 'green'}">
                        <text :style="{color: '#eee'}">Paper</text>
                    </view>
                    <view :style="{flex: 4, alignItems: 'center', paddingTop: 4, height: 30 + 200 * args.item.info.account.trashType.organic / args.item.info.account.scores, backgroundColor: 'blue'}">
                        <text :style="{color: '#eee'}">Organic</text>
                    </view>
                    <view :style="{flex: 4, alignItems: 'center', paddingTop: 4, height: 30 + 200 * args.item.info.account.trashType.plastic / args.item.info.account.scores, backgroundColor: 'black'}">
                        <text :style="{color: '#eee'}">Plastic</text>
                    </view>
                </view>
            </view>
        </flat-list>
    </view>
</template>

<style>
.container {
    align-items: center;
    justify-content: center;
    flex: 1;
    width: 100%;
}
.heading {
    font-size: 30px;
    font-weight: bold;
    color: darkolivegreen;
    margin: 20px;
}
</style>

<script>

import db from './../data/db.json';

export default
{
    data()
    {
        const list = db.residents;
        const index = Math.min(list.length - 1, Math.floor(Math.random() * list.length));
        return {json: [{info: list[index], width: window.innerWidth, height: window.innerHeight}]}
    }
}
</script>