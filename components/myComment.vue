<template>
    <div>
        <div id="comment-list" class="comment-list">
            <!--提交的留言表单-->
            <form action="" class="new-comment">
                <nuxt-link class="avatar" to="/u/123">
                    <img src="../assets/img/default-avatar.jpg">
                </nuxt-link>
                <textarea @focus="send=true" name="" id="" placeholder="写下你的评论..." v-model="value"></textarea>
                <transition :duration="300" name="fade">
                    <div v-if="send" class="write-function-block clearfix">
                        <div class="emoji-modal-wrap">
                            <a href="javascript:void(0)" class="emoji" @click="isShowEmoji">
                                <i class="fa fa-smile-o"></i>
                            </a>
                            <transition :duration="300" name="fade">
                                <div v-if="showEmoji" class="emoji-modal arrow-up">
                                    <vue-emoji @select="selectEmoji"></vue-emoji>
                                </div>
                            </transition>
                        </div>
                        <div class="hint">Ctrl+Enter发表</div>
                        <a href="javascript:void(0)" class="btn btn-send" @click="sendData">发送</a>
                        <a href="javascript:void(0)" class="cancel" @click="send=false">取消</a>
                    </div>
                </transition>

            </form>
            <!--留言的列表-->
            <div class="normal-comment-list" id="normal-comment-list">
                <!--留言的排序-->
                <div class="top-title">
                    <span>25条评论</span>
                    <a href="javascript:void (0)" class="author-only">只看作者</a>
                    <div class="pull-right">
                        <a href="javascript:void (0)" class="active">按喜欢排序</a>
                        <a href="javascript:void (0)">按时间正序</a>
                        <a href="javascript:void (0)">按时间倒序</a>
                    </div>
                </div>
                <!--留言的正文-->
                <div class="comment-placeholder" style="display: none">
                    <div class="author">
                        <div class="avatar"></div>
                        <div class="info">
                            <div class="name"></div>
                            <div class="meta"></div>
                        </div>
                    </div>
                    <div class="title"></div>
                    <div class="title animated-delay"></div>
                    <div class="tool-group">
                        <i class="fa fa-thumbs-o-up"></i>
                        <div class="zan"></div>
                        <i class="fa fa-comment-o"></i>
                        <div class="zan"></div>
                    </div>
                </div>
                <div :id="'comment-'+comment.id" v-for="(comment,index) in comments" class="comment">
                    <div class="comment-content">
                        <div class="author">
                            <nuxt-link to="/u/123" class="avatar">
                                <img :src="comment.user.avatar">
                            </nuxt-link>
                            <div class="info">
                                <nuxt-link class="name" to="/u/123">
                                    {{comment.user.nickname}}
                                </nuxt-link>
                                <div class="meta">
                                    <span>
                                        {{comment.floor}}楼·
                                        {{comment.created_at | formatDate}}
                                    </span>
                                </div>
                            </div>
                        </div>
                        <div class="comment-wrap">
                            <p>
                                {{comment.compiled_content}}
                            </p>
                            <div class="tool-group">
                                <a href="javascript:void (0)">
                                    <i class="fa fa-thumbs-o-up"></i>
                                    <span>{{comment.likes_count}}人点赞</span>
                                </a>
                                <a href="javascript:void (0)" >
                                    <i class="fa fa-comment"></i>
                                    <span>回复</span>
                                </a>
                            </div>
                        </div>
                    </div>
                    <div v-if="comment.children.length != 0" class="sub-comment-list">
                        <div v-for="(subComment,index) in comment.children" :id="'comment-'+subComment.id" class="sub-comment">
                            <p>
                                <nuxt-link to="/u/123">
                                    {{subComment.user.nickname}}
                                </nuxt-link>:
                                <span v-html="subComment.compiled_content"></span>
                            </p>
                            <div class="sub-tool-group">
                                <span>{{subComment.created_at | formatDate}}</span>
                                <a href="javascript:void (0)">
                                    <i class="fa fa-comment-o"></i>
                                    <sapn>回复</sapn>
                                </a>
                            </div>

                        </div>
                        <div class="more-comment">
                            <a href="javascript:void (0)" class="add-comment-btn" @click="showSubCommentForm(index)">
                                <i class="fa fa-pencil"></i>
                                <span>添加新评论</span>
                            </a>
                        </div>
                        <transition :duration="500" name="fade">
                            <form class="new-comment" v-if="activeIndex.includes(index)">
                                <textarea name="" placeholder="写下你的评论..."></textarea>
                                <div class="write-function-block clearfix">
                                    <div class="emoji-modal-wrap">
                                        <a href="javascript:void(0)" class="emoji" @click="showSubEmoji(index)">
                                            <i class="fa fa-smile-o"></i>
                                        </a>
                                        <transition :duration="300" name="fade">
                                            <div v-if="emojiIndex.includes(index)" class="emoji-modal arrow-up">
                                                <vue-emoji @select="selectSubEmoji"></vue-emoji>
                                            </div>
                                        </transition>
                                    </div>
                                    <div class="hint">Ctrl+Enter发表</div>
                                    <a href="javascript:void(0)" class="btn btn-send" @click="sendSubCommentData(index)">发送</a>
                                    <a href="javascript:void(0)" class="cancel" @click="closeSubComment(index)">取消</a>
                                </div>
                            </form>
                        </transition>

                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    import  vueEmoji from  '~/components/vueEmoji'
    export default {
        name: "my-comment",
        data(){
            return {
                send:false,
                showEmoji:false,
                value:'',
                comments:[
                    {
                        id:19935725,
                        floor:2,
                        liked:true,
                        likes_count:12,
                        note_id:23054702,
                        user_id:6780849,
                        user:{
                            avatar:"/default-avatar.jpg",
                            id:6780849,
                            is_author:false,
                            nickname:'七岁就狠拽',
                            badge:null

                        },
                        created_at:'2018-01-25T09:38:14.000+08:00',
                        children_count:4,
                        compiled_content:'今年25岁的我，年纪轻轻月薪就已经达到2800了，加上提成满勤再加上我天生的睿智头脑，平常帮客人拿下拖鞋点下烟得点小费可以拿到3100。觉得自己这几年过得也不容易，现在这么有钱，都不知道怎么花了，开始花钱大手大脚了，以前网吧包夜都是喝自来水，现在敢喝红茶了，还是一晚上买两瓶，甚至打电话出去叫炒河粉而且还要加个鸡蛋，我觉得现在有点迷失自我，有什么办法？希望能回到初心！',
                        children:[
                            {
                                id:20116365,
                                user_id:2604707,
                                user:{
                                    id:2604707,
                                    nickname:"Bowman_",

                                },
                                parent_id:19935725,
                                created_at:"2018-01-30T11:23:03.000+08:00",
                                compiled_content:'兄die,我也和你有着一样的困惑，甚至一度迷失自我...'
                            },
                            {
                                id:20122216,
                                user_id:9933465,
                                user:{
                                    id:9933465,
                                    nickname:"美女荷官",

                                },
                                parent_id:19935725,
                                created_at:"2018-01-30T14:25:32.000+08:00",
                                compiled_content:"是你李大钊飘了,还是我陈独秀拿不动刀了"
                            },
                            {
                                id:20122226,
                                user_id:9964877,
                                user:{
                                    id:9964877,
                                    nickname:"保坤文化传媒",

                                },
                                parent_id:19935725,
                                created_at:"2018-01-30T14:25:49.000+08:00",
                                compiled_content:"哈哈。。"
                            }
                        ]
                    },
                    {
                        id:19935796,
                        floor:3,
                        liked:false,
                        likes_count:2,
                        note_id:23054702,
                        user_id:6780849,
                        user:{
                            avatar:"/default-avatar.jpg",
                            id:6780849,
                            is_author:false,
                            nickname:'七岁就狠拽',
                            badge:null

                        },
                        created_at:"2018-01-25T09:40:18.000+08:00",
                        children_count:3,
                        compiled_content:"作为一名混凝土方块移动工程师，我一直以3000的月薪骄傲，甚至一度迷失自我。。。看了楼主这篇文章，我找回了初心",
                        children:[
                            {
                                id:19949215,
                                user_id:5954136,
                                user:{
                                    id:5954136,
                                    nickname:"与笑颜开",

                                },
                                parent_id:19935796,
                                created_at:"2018-01-25T16:55:40.000+08:00",
                                compiled_content:"混凝土方块移动工程师是啥子工作，我咋没听过？我也做过混凝土这行"
                            },
                            {
                                id:20062029,
                                user_id:8914781,
                                user:{
                                    id:8914781,
                                    nickname:"向天再借5厘米"

                                },
                                parent_id:19935796,
                                created_at:"2018-01-28T21:06:14.000+08:00",
                                compiled_content:
                                "@与笑颜开搬砖"
                            },
                            {
                                id:20122231,
                                user_id:9964877,
                                user:{
                                    id:9964877,
                                    nickname:"保坤文化传媒"

                                },
                                parent_id:19935796,
                                created_at:"2018-01-30T14:26:00.000+08:00",
                                compiled_content:"好有意思。"
                            }

                        ]
                    },
                    {
                        id:20080144,
                        floor:4,
                        liked:false,
                        likes_count:2,
                        note_id:23054702,
                        user_id:3160769,
                        user:{
                            avatar:"/default-avatar.jpg",
                            id:3160769,
                            is_author:false,
                            nickname:"yuebiubiu",
                            badge:null

                        },
                        created_at:'2018-01-29T11:26:53.000+08:00',
                        children_count:0,
                        compiled_content:"楼上评论的都是大佬啊",
                        children:[]
                    }
                ],
                activeIndex:[],
                emojiIndex:[]
            }
        },
        methods:{
            isShowEmoji:function () {
                this.showEmoji =  !this.showEmoji;
                // console.log(this.showEmoji);
            },
            selectEmoji:function (code) {
                this.showEmoji = false;
                this.value += code;

            },
            sendData:function () {
                console.log('发送value值的数据给后端')
            },
            showSubCommentForm:function (value) {
                if(this.activeIndex.includes(value)){
                    let index = this.activeIndex.indexOf(value);
                    this.activeIndex.splice(index,1);
                }else {
                    this.activeIndex.push(value);
                }

            },
            sendSubCommentData:function (value) {
                let index = this.activeIndex.indexOf(value);
                this.activeIndex.splice(index,1);
            },
            closeSubComment:function (value) {
                let index = this.activeIndex.indexOf(value);
                this.activeIndex.splice(index,1);
            },
            showSubEmoji:function (value) {
                if(this.emojiIndex.includes(value)){
                    let index = this.emojiIndex.indexOf(value);
                    this.emojiIndex.splice(index,1);
                }else{
                    this.emojiIndex.push(value);
                }
            },
            selectSubEmoji:function () {

            }

        },
        directives:{
            "focus":{
                bind:function (el,binding,Vnode,oldVnode) {

                }
            },
            "form":{
                update:function (el) {

                }
            }
        },
        components:{
            vueEmoji
        }
    }
</script>

<style scoped>
    .fade-enter-active,.fade-leave-active{
        opacity: 1;
        transition: .3s;
        -webkit-transition: .3s;
    }
    .fade-enter,.fade-leave-to{
        opacity: 0;
        transform:translate3d(0,-5%,0);
        -webkit-transform: translate3d(0,-5%,0);
        transition: .3s;
        -webkit-transition: .3s;
    }
    .note .post .comment-list{
        padding-top: 20px;
    }
    .note .post .comment-list .new-comment{
        position: relative;
        margin-left: 48px;
        margin-bottom: 20px;
    }
    .note .post .comment-list .avatar{
        width: 38px;
        height: 38px;
        display: inline-block;
        margin-right: 5px;

    }
    .note .post .comment-list .new-comment .avatar{
        position: absolute;
        left: -48px;
    }
    .note .post .comment-list .new-comment textarea{
        width: 100%;
        height: 80px;
        padding: 10px 15px;
        border: 1px solid #ccc;
        border-radius: 4px;
        display: inline-block;
        vertical-align: top;
        outline-style: none;
        resize: none;
        background-color: #f8f8f8;
        font-size: 13px;
    }
    .note .post .comment-list .new-comment .emoji-modal-wrap{
        position: relative;
    }
    .note .post .comment-list .new-comment .emoji{
        float: left;
        margin-top: 20px;
    }
    .note .post .comment-list .new-comment .emoji i{
        font-size: 20px;
        color: #969696;
    }
    .note .post .comment-list .new-comment .emoji i:hover{
        color: #333333;
    }
    .note .post .comment-list .new-comment .hint{
        float: left;
        margin: 22px 0 0 20px;
        font-size: 13px;
        color: #969696;
    }
    .note .post .comment-list .new-comment .cancel{
        float: right;
        font-size: 16px;
        margin: 18px 30px 0 0 ;
        color: #969696!important;
    }
    .note .post .comment-list .new-comment .cancel:hover{
        color: #333333!important;
    }
    .note .post .comment-list .new-comment .btn-send{
        float: right;
        width: 78px;
        padding: 8 18px;
        margin: 10px 0;
        font-size: 18px;
        background: #42c02e;
        border-radius: 20px;
        color: #fff!important;
        box-shadow: none;
    }
    .note .post .comment-list .new-comment .btn-send:hover{
        background: #3db922;
    }
    .note .post .comment-list .new-comment .emoji-modal-wrap .emoji-modal{
        position: absolute;
        top: 50px;
        left: -48px;
        width: 402px;
        height: 208px;
        padding: 10px;
        border: 1px solid #d9d9d9;
        border-radius: 4px;
        box-shadow: 0 5px 25px rgba(0,0,0,.1);
        z-index: 999999;
        background: #fff;
    }
    .arrow-up:after{
        content: "";
        position: absolute;
        height: 15px;
        width: 15px;
        border-left: 1px solid #d9d9d9;
        border-top: 1px solid #d9d9d9;
        transform: translate3d(0,-50%,0) rotate(45deg);
        -webkit-transform: translate3d(0,-50%,0) rotate(45deg);
        position: absolute;
        left: 48px;
        top: -1px;
        background: #fff;
    }
    .note .post .comment-list .normal-comment-list{
        margin-top: 30px;
    }
    .note .post .comment-list .top-title{
        padding-bottom: 20px;
        border-bottom: 1px solid #f0f0f0;
    }
    .note .post .comment-list .top-title span{
        font-size: 17px;
        font-weight: 700;
    }
    .note .post .comment-list .top-title .author-only{
        font-size: 14px;
        padding: 4px 8px;
        border: 1px solid #e1e1e1;
        border-radius:12px;
        color: #969696!important;
        margin-left: 10px;
    }
    .note .post .comment-list .top-title .pull-right a{
        margin-left: 10px;
        font-size: 12px;
        color: #969696!important;
    }
    .note .post .comment-list .top-title .pull-right a.active{
        color: #2f2f2f!important;
    }
    .note .post .comment-list .top-title .pull-right a:hover{
        color: #2f2f2f!important;
    }
    .note .post .comment-list .comment{
        padding: 20px 0 30px 0;
        border-bottom: 1px solid #f0f0f0;
    }
    .note .post .comment-list .comment .author{
        margin-bottom: 15px;
    }
    .note .post .comment-list .info{
        display: inline-block;
        vertical-align: middle;
    }
    .note .post .comment-list .info .name{
        font-size: 15px;
    }
    .note .post .comment-list .info .meta{
        font-size: 12px;
        color: #969696;
    }
    .note .post .comment-list .comment p{
        font-size: 16px;
        margin: 10px 0;
        line-height: 1.5;
        word-break: break-all!important;
    }
    .note .post .comment-list .comment .tool-group a{
        color: #969696!important;
        margin-right: 15px;
    }
    .note .post .comment-list .comment .tool-group a i{
        font-size: 18px;
        margin-right: 5px;
    }
    .note .post .comment-list .comment .tool-group a span{
        font-size: 14px;
    }
    .note .post .comment-list .sub-comment-list{
        border-left: 2px solid #d9d9d9;
        margin-top: 10px;
        padding: 5px 0 5px 20px;
    }
    .note .post .comment-list .sub-comment{
        padding-bottom: 15px;
        margin-bottom: 15px;
        border-bottom: 1px dashed #f0f0f0;
    }
    .note .post .comment-list .sub-comment p{
        font-size: 14px;
        line-height: 1.5px;
        margin-bottom: 15px;
    }
    .note .post .comment-list .sub-comment a{
        color: #3194d0!important;
    }
    .note .post .comment-list .sub-tool-group{
        font-size: 12px;
        color: #969696;
    }
    .note .post .comment-list .sub-tool-group a{
        margin-left: 10px;
        color: #969696!important;
    }
    .note .post .comment-list .sub-tool-group a i{
        margin-right: 5px;
    }
    .note .post .comment-list .more-comment{
        font-size: 14px;
        color: #969696;
    }
    .note .post .comment-list .more-comment:hover{
        color: #333;
    }
    .note .post .comment-list .more-comment i{
        margin-right: 10px;
    }
    .note .post .comment .new-comment{
        margin: 20px 0 0 0;
    }
</style>