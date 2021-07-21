<template>
    <view class="content">
        <view class="title">{{title}}</view>
        <view class="art-content">
            <!-- 获取的数据是html形式，有<p></p>标签，不能直接使用。可以使用<rich-text></rich-text> -->
            <rich-text class="richText" :nodes="strings">{{strings}}</rich-text>
        </view>
    </view>
</template>

<script>
    export default {
        data() {
            return {
                title: '',
                strings: ''
            }
        },
        onLoad: function (e) {
            console.log(e);
            uni.request({
                url: 'https://unidemo.dcloud.net.cn/api/news/36kr/'+e.newsid,
                method: 'GET',
                data: {},
                success: res => {
                    console.log(res);
                    this.title = res.data.title;
                    this.strings = res.data.content;
                },
                fail: () => {},
                complete: () => {}
            });
        },
        methods: {
            
        }
    }
</script>

<style>
.content {
    padding: 10rpx 2%;
    width: 96%;
    flex-wrap: wrap;
}
.title {
    line-height: 2em;
    font-weight: 700;
    font-size: 38rpx;
}
.art-content {
    line-height: 2em;
}
</style>
