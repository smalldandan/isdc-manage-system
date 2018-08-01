<template>
    <!--走马灯显示公告面板-->
    <el-carousel indicator-position="outside">
        <el-carousel-item v-for="(item, index) in marqueeList">
            <!--{{item.title}}-->
            <!--<br>-->
            <!--{{item.subtitle}}-->
            <!--<br>-->
            <!--{{item.brief_introduction}}-->
            <!--<br>-->
            <!--{{item.content}}-->
            <!--<br>-->
            <!--{{item.time}}-->
            <!--<br>-->
            <!--{{item.people}}-->
            <article class="uk-article">
                <h1 class="uk-article-title">{{item.title}}</h1>
                <p class="uk-article-meta">{{item.subtitle}}</p>
                <p class="uk-article-lead">{{item.brief_introduction}}</p>
                {{item.content}}
                <hr class="uk-article-divider">
                ...
            </article>
        </el-carousel-item>



    </el-carousel>
</template>

<script>
    import Vue from 'vue';

    export default {
        name: "board",
        data() {
            return {
                url: '/api/board',
                tableData: [],
                formLabelWidth: '120px',
                form: {},
                editing: 0,
                //marquee，字幕表,存储公告信息的列表
                marqueeList: [
                    {
                        title: '“科研成果工作培训会”在我院举行',
                        subtitle:'公告一的子标题',
                        brief_introduction:'这是公告一的简介。。。。。。',
                        content: '这是公告一的内容',
                        time: '2018.8.1',
                        people: 'tom'
                    },
                    {
                        title: '公告二',
                        subtitle:'公告二的子标题',
                        brief_introduction:'',
                        content: '这是公告二的内容',
                        time: '2018.8.2',
                        people: 'jack'
                    },
                    {
                        title: '公告三',
                        subtitle:'',
                        brief_introduction:'',
                        content: '这是公告三的内容',
                        time: '2018.8.3',
                        people: 'rose'
                    },
                    {
                        title: '公告四',
                        subtitle:'',
                        brief_introduction:'',
                        content: '这是公告四的内容',
                        time: '2018.8.4',
                        people: 'lvge'
                    },
                ],
            }
        }
    }
</script>

<style scoped>
    /*.handle-box {*/
        /*margin-bottom: 20px;*/
    /*}*/
    /*.el-carousel__item h3 {*/
        /*color: #475669;*/
        /*font-size: 18px;*/
        /*opacity: 0.75;*/
        /*line-height: 300px;*/
        /*margin: 0;*/
    /*}*/

    /*.el-carousel__item:nth-child(2n) {*/
        /*background-color: #99a9bf;*/
    /*}*/

    /*.el-carousel__item:nth-child(2n+1) {*/
        /*background-color: #d3dce6;*/
    /*}*/
</style>
