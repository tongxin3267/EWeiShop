<template>
    <div class='character'>
        <page-info theme='EWEISHOP 店铺装修的特色' detail=''>
            <ul class='character-list'>
                <li class='character-list__item' v-for='(item,index) in list' :key='index'>
                    <img v-lazy="item.img" :alt="item.detail">
                    <h4>{{item.title}}</h4>
                    <span v-html='item.detail'></span>
                </li>
            </ul>
        </page-info>
    </div>
</template>

<script>
    import pageInfo from '../retail/PageMiddleInfo'
    export default {
        components: {
            pageInfo
        },
        data() {
            return {
                list: [{
                    img: '/static/image/renovation/character1.jpg',
                    title: '易拖拽操作',
                    detail: '首次接触电商<br/>即可快速掌握技巧'
                }, {
                    img: '/static/image/renovation/character2.jpg',
                    title: '装修效率倍增',
                    detail: '装修页面一键应用<br/>全渠道统一样式'
                }, {
                    img: '/static/image/renovation/character3.jpg',
                    title: '个性化装修',
                    detail: '组件自由拖拽满足<br/>商城个性化需求'
                }]
            }
        },
    }
</script>

<style scoped lang='scss'>
    .character {
        width: 100%;
        background: #fafafa;
        .character-list {
            width: 100%;
            display: flex;
            justify-content: center;
            box-shadow: #e5e4e4 0 0 16px 50%;
            margin: 60px 0 70px;
            >.character-list__item {
                box-shadow: 0 4px 14px rgba(0, 0, 0, 0.08);
                width: 211px;
                height: 292px;
                background: #fff;
                position: relative;
                margin: 0 9px;
                display: flex;
                justify-content: center;
                flex-wrap: wrap;
                >img {
                    width: 78px;
                    margin-top: 36px;
                    height: 77px;
                }
                &:nth-child(2)>img {
                    width: 95px;
                }
                >h4,
                >span {
                    position: absolute;
                    width: 100%;
                    text-align: center;
                }
                >h4 {
                    font-size: 26px;
                    color: #3b426b;
                    line-height: 26px;
                    top: 150px;
                    font-weight: 600;
                }
                >span {
                    font-size: 24px;
                    color: #7b88a2;
                    line-height: 39px;
                    top: 192px;
                    transform: scale(.9);
                }
            }
        }
    }
</style>