<template>
    <div class='brief-bg'>
        <swipe :autoplay="3000" style='height:100%;' indicator-color="white" @change="onChange">
            <swipe-item class='vip-manage-easier__swipe-item' v-for="(item,index) in swipeList" :key='index'>
                <div v-if="item.theme!==''">
                    <img class='brief__bgImg' v-lazy="'/static/image/customerService/banner-bg.png'" alt="">
                    <div class='brief-bg__word'>
                        <h2>{{item.theme}}</h2>
                        <span>{{item.detail}}</span>
                    </div>
                    <img v-lazy="item.img" class='brief-bg__img' :alt="item.detail">
                </div>
                <div v-else>
                    <img v-lazy="item.img" alt="" style="max-width:100%;" @click="goServiceActive()">
                </div>
            </swipe-item>
            <div class="custom-indicator" slot="indicator">
                <span class="point point1" v-for="(item,index) in swipeList" :key='index' :class='{"active-point":index==current}'></span>
            </div>
        </swipe>
    </div>
</template>

<script>
    import {
        Swipe,
        SwipeItem
    } from 'vant';
    import {
        request
    } from 'http';
    export default {
        components: {
            Swipe,
            SwipeItem
        },
        data() {
            return {
                current: 0,
                detailLeftAlign: {
                    textAlign: 'left'
                },
                swipeList: [
                //     {
                //     img: '/static/image/index/banner350.png',
                //     theme: '',
                //     detail: ''
                // }, 
                {
                    img: '/static/image/customerService/banner-img.png',
                    theme: '在线客服系统',
                    detail: '加强商家与客户之间的沟通,是网络营销最重要的工具'
                }]
            }
        },
        methods: {
            onChange(index) {
                this.current = index;
            },
            goServiceActive() {
                this.$router.push({
                    path: '/custormServiceActive'
                })
            }
        }
    }
</script>

<style scoped lang='scss'>
    .brief-bg {
        width: 100%;
        height: 350px;
        position: relative;
        background: linear-gradient(45deg, #ff654c, #fb6638);
        .brief__bgImg {
            width: 100%;
        }
        .brief-bg__word {
            position: absolute;
            width: 340px;
            left: 40px;
            top: 112px;
            color: #fff;
            overflow: hidden;
            >h2 {
                font-weight: 600;
                font-size: 36px;
                color: #fff;
                margin-bottom: 40px;
            }
            >span {
                font-size: 24px;
                color: rgba(255, 255, 255, 0.8);
                line-height: 42px;
            }
        }
        .brief-bg__img {
            width: 255px;
            position: absolute;
            top: 50px;
            right: 32px;
        }
        .custom-indicator {
            position: absolute;
            bottom: 24px;
            left: 50%;
            transform: translate(-50%, 0);
            >.point {
                box-sizing: border-box;
                width: 4px;/*no*/
                height: 4px;/*no*/
                border-radius: 4px;
                float: left;
                margin-right: 6px;
                transition: all 0.3s;
                background: rgba(255, 255, 255, 0.5);
            }
            >.active-point {
                width: 18px;
                background: #ddd;
            }
        }
    }
</style>