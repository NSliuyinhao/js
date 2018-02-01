<template>
    <div>
        <my-header></my-header>
        <div class="index my-container">
            <div class="row">
                <div class="col-8 main">
                    <!--banner-->
                    <div class="banner">
                        <div v-swiper:mySwiper="swiperOption">
                            <div class="swiper-wrapper">
                                <div class="swiper-slide" v-for="banner in banners">
                                    <img :src="banner">
                                </div>
                            </div>
                            <div class="swiper-pagination swiper-pagination-white"></div>
                            <div class="swiper-button-prev swiper-button-white"></div>
                            <div class="swiper-button-next swiper-button-white"></div>
                        </div>
                    </div>
                    <!--推荐专题-->
                    <div class="recomment-collection">
                        <nuxt-link to="/collection/123">
                            <img src="../assets/img/collection1.png" alt="">
                            <span>文学</span>
                        </nuxt-link>
                        <nuxt-link to="/collection/123">
                            <img src="../assets/img/collection2.jpg" alt="">
                            <span>手绘</span>
                        </nuxt-link>
                        <nuxt-link to="/collection/123">
                            <img src="../assets/img/collection3.jpg" alt="">
                            <span>@IT·互联网</span>
                        </nuxt-link>
                        <nuxt-link to="/collection/123">
                            <img src="../assets/img/collection1.png" alt="">
                            <span>文学</span>
                        </nuxt-link>
                        <nuxt-link to="/collection/123">
                            <img src="../assets/img/collection3.jpg" alt="">
                            <span>@IT·互联网</span>
                        </nuxt-link>
                        <nuxt-link to="/collection/123">
                            <img src="../assets/img/collection2.jpg" alt="">
                            <span>手绘</span>
                        </nuxt-link>
                        <nuxt-link to="/collection/123">
                            <img src="../assets/img/collection3.jpg" alt="">
                            <span>@IT·互联网</span>
                        </nuxt-link>
                        <nuxt-link to="/collection/123">
                            <img src="../assets/img/collection3.jpg" alt="">
                            <span>@IT·互联网</span>
                        </nuxt-link>
                        <nuxt-link to="/collection/123">
                            <img src="../assets/img/collection3.jpg" alt="">
                            <span>@IT·互联网</span>
                        </nuxt-link>
                        <nuxt-link to="/collection/123" class="more-hot-collection">
                            更多热门专题
                            <i class="fa fa-angle-right"></i>
                        </nuxt-link>
                    </div>
                    <div class="split-line"></div>
                    <!--文章列表-->
                    <div id="list-container">
                        <ul class="note-list">
                            <li class="have-img">
                                <nuxt-link class="wrap-img" to="/p/123">
                                    <img src="../assets/img/pic.jpg">
                                </nuxt-link>
                                <div class="content">
                                    <div class="author">
                                        <nuxt-link to="/u/123" class="avatar">
                                            <img src="../assets/img/default-avatar.jpg">
                                        </nuxt-link>
                                        <div class="info">
                                            <nuxt-link to="/u/123" class="nickname">
                                                测试用户
                                            </nuxt-link>
                                            <span class="time">8小时前</span>
                                        </div>
                                    </div>
                                    <nuxt-link class="title" to="/p/123">
                                        如何把书中的知识转化成能力?这是我见过最好的回答
                                    </nuxt-link>
                                    <p class="abstract">
                                        随着知识经济的兴起，读书的重要性得到了大家的普
                                        同，于是市场上出现很多读书方法，比如速度、多读
                                        慢读、列读……不管你采用哪一种读书方法，最终都要
                                        归到“行动”二字上，正如陆...
                                    </p>
                                    <div class="meta">
                                        <nuxt-link to="/collection/123" class="collection-tag">短篇小说</nuxt-link>
                                        <nuxt-link to="/p/123" class="tag">
                                            <i class="fa fa-eye"></i>
                                            597
                                        </nuxt-link>
                                        <nuxt-link to="/p/123" class="tag">
                                            <i class="fa fa-comment"></i>
                                            200
                                        </nuxt-link>
                                        <span>
                                            <i class="fa fa-heart"></i>
                                            546
                                        </span>
                                    </div>
                                </div>
                            </li>
                            <li>
                                <div class="content">
                                    <div class="author">
                                        <nuxt-link to="/u/123" class="avatar">
                                            <img src="../assets/img/default-avatar.jpg">
                                        </nuxt-link>
                                        <div class="info">
                                            <nuxt-link to="/u/123" class="nickname">
                                                测试用户
                                            </nuxt-link>
                                            <span class="time">8小时前</span>
                                        </div>
                                    </div>
                                    <nuxt-link class="title" to="/p/123">
                                        如何把书中的知识转化成能力?这是我见过最好的回答
                                    </nuxt-link>
                                    <p class="abstract">
                                        随着知识经济的兴起，读书的重要性得到了大家的普
                                        同，于是市场上出现很多读书方法，比如速度、多读
                                        慢读、列读……不管你采用哪一种读书方法，最终都要
                                        归到“行动”二字上，正如陆...
                                    </p>
                                    <div class="meta">
                                        <nuxt-link to="/collection/123" class="collection-tag">短篇小说</nuxt-link>
                                        <nuxt-link to="/p/123" class="tag">
                                            <i class="fa fa-eye"></i>
                                            597
                                        </nuxt-link>
                                        <nuxt-link to="/p/123" class="tag">
                                            <i class="fa fa-comment"></i>
                                            200
                                        </nuxt-link>
                                        <span>
                                            <i class="fa fa-heart"></i>
                                            546
                                        </span>
                                    </div>
                                </div>
                            </li>
                            <li class="have-img">
                                <nuxt-link class="wrap-img" to="/p/123">
                                    <img src="../assets/img/pic.jpg">
                                </nuxt-link>
                                <div class="content">
                                    <div class="author">
                                        <nuxt-link to="/u/123" class="avatar">
                                            <img src="../assets/img/default-avatar.jpg">
                                        </nuxt-link>
                                        <div class="info">
                                            <nuxt-link to="/u/123" class="nickname">
                                                测试用户
                                            </nuxt-link>
                                            <span class="time">8小时前</span>
                                        </div>
                                    </div>
                                    <nuxt-link class="title" to="/p/123">
                                        如何把书中的知识转化成能力?这是我见过最好的回答
                                    </nuxt-link>
                                    <p class="abstract">
                                        随着知识经济的兴起，读书的重要性得到了大家的普
                                        同，于是市场上出现很多读书方法，比如速度、多读
                                        慢读、列读……不管你采用哪一种读书方法，最终都要
                                        归到“行动”二字上，正如陆...
                                    </p>
                                    <div class="meta">
                                        <nuxt-link to="/collection/123" class="collection-tag">短篇小说</nuxt-link>
                                        <nuxt-link to="/p/123" class="tag">
                                            <i class="fa fa-eye"></i>
                                            597
                                        </nuxt-link>
                                        <nuxt-link to="/p/123" class="tag">
                                            <i class="fa fa-comment"></i>
                                            200
                                        </nuxt-link>
                                        <span>
                                            <i class="fa fa-heart"></i>
                                            546
                                        </span>
                                    </div>
                                </div>
                            </li>
                            <li>
                                <div class="content">
                                    <div class="author">
                                        <nuxt-link to="/u/123" class="avatar">
                                            <img src="../assets/img/default-avatar.jpg">
                                        </nuxt-link>
                                        <div class="info">
                                            <nuxt-link to="/u/123" class="nickname">
                                                测试用户
                                            </nuxt-link>
                                            <span class="time">8小时前</span>
                                        </div>
                                    </div>
                                    <nuxt-link class="title" to="/p/123">
                                        如何把书中的知识转化成能力?这是我见过最好的回答
                                    </nuxt-link>
                                    <p class="abstract">
                                        随着知识经济的兴起，读书的重要性得到了大家的普
                                        同，于是市场上出现很多读书方法，比如速度、多读
                                        慢读、列读……不管你采用哪一种读书方法，最终都要
                                        归到“行动”二字上，正如陆...
                                    </p>
                                    <div class="meta">
                                        <nuxt-link to="/collection/123" class="collection-tag">短篇小说</nuxt-link>
                                        <nuxt-link to="/p/123" class="tag">
                                            <i class="fa fa-eye"></i>
                                            597
                                        </nuxt-link>
                                        <nuxt-link to="/p/123" class="tag">
                                            <i class="fa fa-comment"></i>
                                            200
                                        </nuxt-link>
                                        <span>
                                            <i class="fa fa-heart"></i>
                                            546
                                        </span>
                                    </div>
                                </div>
                            </li>
                            <li class="have-img">
                                <nuxt-link class="wrap-img" to="/p/123">
                                    <img src="../assets/img/pic.jpg">
                                </nuxt-link>
                                <div class="content">
                                    <div class="author">
                                        <nuxt-link to="/u/123" class="avatar">
                                            <img src="../assets/img/default-avatar.jpg">
                                        </nuxt-link>
                                        <div class="info">
                                            <nuxt-link to="/u/123" class="nickname">
                                                测试用户
                                            </nuxt-link>
                                            <span class="time">8小时前</span>
                                        </div>
                                    </div>
                                    <nuxt-link class="title" to="/p/123">
                                        如何把书中的知识转化成能力?这是我见过最好的回答
                                    </nuxt-link>
                                    <p class="abstract">
                                        随着知识经济的兴起，读书的重要性得到了大家的普
                                        同，于是市场上出现很多读书方法，比如速度、多读
                                        慢读、列读……不管你采用哪一种读书方法，最终都要
                                        归到“行动”二字上，正如陆...
                                    </p>
                                    <div class="meta">
                                        <nuxt-link to="/collection/123" class="collection-tag">短篇小说</nuxt-link>
                                        <nuxt-link to="/p/123" class="tag">
                                            <i class="fa fa-eye"></i>
                                            597
                                        </nuxt-link>
                                        <nuxt-link to="/p/123" class="tag">
                                            <i class="fa fa-comment"></i>
                                            200
                                        </nuxt-link>
                                        <span>
                                            <i class="fa fa-heart"></i>
                                            546
                                        </span>
                                    </div>
                                </div>
                            </li>
                            <li>
                                <div class="content">
                                    <div class="author">
                                        <nuxt-link to="/u/123" class="avatar">
                                            <img src="../assets/img/default-avatar.jpg">
                                        </nuxt-link>
                                        <div class="info">
                                            <nuxt-link to="/u/123" class="nickname">
                                                测试用户
                                            </nuxt-link>
                                            <span class="time">8小时前</span>
                                        </div>
                                    </div>
                                    <nuxt-link class="title" to="/p/123">
                                        如何把书中的知识转化成能力?这是我见过最好的回答
                                    </nuxt-link>
                                    <p class="abstract">
                                        随着知识经济的兴起，读书的重要性得到了大家的普
                                        同，于是市场上出现很多读书方法，比如速度、多读
                                        慢读、列读……不管你采用哪一种读书方法，最终都要
                                        归到“行动”二字上，正如陆...
                                    </p>
                                    <div class="meta">
                                        <nuxt-link to="/collection/123" class="collection-tag">短篇小说</nuxt-link>
                                        <nuxt-link to="/p/123" class="tag">
                                            <i class="fa fa-eye"></i>
                                            597
                                        </nuxt-link>
                                        <nuxt-link to="/p/123" class="tag">
                                            <i class="fa fa-comment"></i>
                                            200
                                        </nuxt-link>
                                        <span>
                                            <i class="fa fa-heart"></i>
                                            546
                                        </span>
                                    </div>
                                </div>
                            </li>
                        </ul>
                    </div>
                    <!--阅读更多-->
                    <nuxt-link to="/" class="load-more">阅读更多</nuxt-link>
                </div>
                <div class="col-4 aside">
                    <div class="board">
                        <nuxt-link to="/">
                            <img src="../assets/img/xsb.png" alt="">
                        </nuxt-link>
                        <nuxt-link to="/">
                            <img src="../assets/img/weekhot.png" alt="">
                        </nuxt-link>
                        <nuxt-link to="/">
                            <img src="../assets/img/mounthhot.png" alt="">
                        </nuxt-link>
                        <nuxt-link to="/">
                            <img src="../assets/img/jscbs.png" alt="">
                        </nuxt-link>
                        <nuxt-link to="/">
                            <img src="../assets/img/jsdxt.png" alt="">
                        </nuxt-link>
                    </div>
                    <nuxt-link class="download" to="/">
                        <img src="../assets/img/collection3.jpg" alt="">
                        <div class="info">
                            <div class="title">扫码加微信
                            <i class="fa fa-angle-right"></i></div>
                            <div class="description">随时随地的发现和创作</div>
                        </div>
                    </nuxt-link>
                    <div class="recomment-author">
                        <div class="title">
                            <span>推荐作者</span>
                            <a class="page-change" href="javascript:void(0)" @click="rotate">
                                <i ref="refresh" class="fa fa-refresh"></i>换一批
                            </a>
                        </div>
                        <ul class="list">
                            <li>
                                <nuxt-link class="avatar" to="/u/123">
                                    <img src="../assets/img/default-avatar.jpg" alt="">
                                </nuxt-link>
                                <nuxt-link class="follow" to="/u/123">
                                    <i class="fa fa-plus-square-o"></i>
                                    关注
                                </nuxt-link>
                                <nuxt-link class="name" to="/u/123">战小狼</nuxt-link>
                                <p>写了152.9k字·7.2k喜欢</p>
                            </li>
                            <li>
                                <nuxt-link class="avatar" to="/u/123">
                                    <img src="../assets/img/default-avatar.jpg" alt="">
                                </nuxt-link>
                                <nuxt-link class="follow" to="/u/123">
                                    <i class="fa fa-plus-square-o"></i>
                                    关注
                                </nuxt-link>
                                <nuxt-link class="name" to="/u/123">战小狼</nuxt-link>
                                <p>写了152.9k字·7.2k喜欢</p>
                            </li>
                            <li>
                                <nuxt-link class="avatar" to="/u/123">
                                    <img src="../assets/img/default-avatar.jpg" alt="">
                                </nuxt-link>
                                <nuxt-link class="follow" to="/u/123">
                                    <i class="fa fa-plus-square-o"></i>
                                    关注
                                </nuxt-link>
                                <nuxt-link class="name" to="/u/123">战小狼</nuxt-link>
                                <p>写了152.9k字·7.2k喜欢</p>
                            </li>
                        </ul>
                        <nuxt-link to="/" class="find-more">查看全部<i class="fa fa-angle-right fa-x"></i></nuxt-link>
                    </div>
                </div>
            </div>
        </div>
        <footer class="my-container">
            <div class="row">
                <div class="col-8 .footer">
                    <ul class="footer-list">
                        <li>作者:刘银豪</li>
                        <li>电话:188******53</li>
                        <li>邮箱:6102*****@qq.com</li>
                    </ul>
                    <p>创作你的创作</p>
                </div>
            </div>
        </footer>
    </div>
</template>
<script>
    import myHeader from '~/components/myHeader'
    export default {
        data(){
            return {
                banners: [
                    '/lunbo1.jpg',
                    '/lunbo2.jpg',
                    '/lunbo3.jpg',
                    '/lunbo4.jpg'
                ],
                swiperOption: {
                    loop: true,
                    slidesPerView: 'auto',
                    centeredSlides: true,
                    spaceBetween: 30,
                    autoplay: {
                        delay: 3000,
                        stopOnLastSlide: false,//是否停止在最后一张
                        disableOnInteraction: false,//禁止轮播
                    },
                    pagination: {
                        el: '.swiper-pagination',
                        dynamicBullets: true
                    },
                    navigation: {
                        nextEl: '.swiper-button-next',
                        prevEl: '.swiper-button-prev'
                    }
                },
                deg:0
            }
        },
        components:{
            myHeader
        },
        mounted(){

        },
        methods:{
            rotate:function () {
                this.deg = this.deg + 360;
                this.$refs.refresh.style.transform = `rotate(${this.deg}deg)`
            }
        }

    }
</script>
<style>
</style>