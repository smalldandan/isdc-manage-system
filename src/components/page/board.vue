<template>
    <!--走马灯显示公告面板-->
    <el-carousel indicator-position="outside" :interval="4000" type="card" height="400px">
        <el-carousel-item v-for="(item, index) in form">


            <div class="el-row" style="margin-left: -10px; margin-right: -10px;">
                <div class="el-col el-col-12 el-col-offset-6" style="padding-left: 10px; padding-right: 10px;">
                    <br><br>
                    <article class="uk-article">
                        <h1 class="uk-article-title" style="font-size: 30px">{{item.title}}</h1>
                        <p class="uk-article-meta">发布日期：{{item.releaseDate}}</p>
                        <!--<p class="uk-article-lead">{{item.brief_introduction}}</p>-->
                        <p>
                            {{item.content}}
                        </p>
                        <a @click="link(item.href)">继续阅读</a>
                    </article>
                </div>
            </div>
            <!--<br><br>-->


        </el-carousel-item>
    </el-carousel>
</template>

<script>
    import Vue from 'vue';

    export default {
        name: "board",
        data() {
            return {
                url: '/Announce/list',
                tableData: [],
                formLabelWidth: '120px',
                form: {
                    /*id: '',
                    title: '',
                    releaseDate: '',
                    enabled: '',
                    content: ''*/
                },
                editing: 0,
                //marquee，字幕表,存储公告信息的列表
                marqueeList: [
                    {
                        id:'',
                        title: '“《炉石传说》全新扩展包“砰砰计划”现已公布 ',
                        content: '一起加入砰砰实验室团队，探寻科研生活中的神奇机遇',
                        releaseDate: '2018-7-11',
                        href: 'http://hs.blizzard.cn/article/16/13504'
                    },
                    {
                        id:'',
                        title: '“2018ChinaJoy暴雪展台试玩活动前瞻',
                        content: '一年一度的ChinaJoy又将到来，今年的暴雪游戏展台准备了丰富的试玩活动等你来体验！想要抢先试玩《魔兽世界》、《炉石传说》的全新版本吗？想和真人大小的“猎空”雕像合影吗？那就快来加入我们吧！此外你还能感受到真实还原的游戏场景，并参与丰富的试玩活动赢取精美礼品！',
                        releaseDate: '2018-7-30',
                        href: 'http://hs.blizzard.cn/article/13/13714'
                    },
                    {
                        id:'',
                        title: '《炉石传说》炉边闲谈——2018年7月31日',
                        content: '欢迎来到《炉石传说》炉边闲谈，我们将在这里与大家分享一些玩家们提出的问题！',
                        releaseDate: '2018-7-31',
                        href: 'http://bbs.hs.blizzard.cn/forum.php?mod=viewthread&tid=677534&page=1&extra=#pid2555850'
                    },
                    {
                        id:'',
                        title: ' 排名对战2018年八月赛季——柠檬冰饮',
                        content: '《炉石传说》2018年八月对战赛季已经打响——而我们又将为大家带来新的卡牌背面图案！',
                        releaseDate: '2018-8-1',
                        href: 'http://hs.blizzard.cn/article/16/13723'
                    }
                ],
            }
        },
        created() {
            this.getData();
        },
        methods: {
            link(e) {
                window.location.href = e;
            },
            getData(){
                let self = this;
                self.$http.get(self.url).then((res) => {
                    res.json().then(data => self.marqueeList = data.data);
                });

            }
        }
    }
</script>

<style scoped>

    .el-carousel__item h3 {
        color: #475669;
        font-size: 14px;
        opacity: 0.75;
        line-height: 200px;
        margin: 0;
    }

    .el-carousel__item:nth-child(2n) {
        background-color: #99a9bf;
    }

    .el-carousel__item:nth-child(2n+1) {
        background-color: #d3dce6;
    }
</style>
