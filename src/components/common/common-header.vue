<template>
    <el-row >
        <el-col>
            <el-row class="common-header" style="height: 82px;z-index:45">

                <!--PC端导航开始-->
                <el-col class="head hidden-xs-only" id="head">
                    <el-row>
                        <el-col class="block hidden-md-and-down" :lg="1" :xl="3">&nbsp;</el-col>
                        <el-col class="header-logo hidden-xs-only" :sm="4" :md="4" :lg="3" :xl="4">
                            <a href="/">
                                <!--不进行跳转-->
                                <div class="logo-img"></div>
                            </a>
                        </el-col>
                        <el-col class="nav hidden-xs-only" :sm="20" :md="20" :lg="19" :xl="14">
                            <ul class="nav_pc">
                                <li>
                                    <a class="a1" href="javascript:;">WHAT WE DO</a>
                                </li>
                                <li>
                                    <a class="a1" href="/team">TEAM</a>
                                </li>
                                <li>
                                    <a class="a1" href="/caseStudies">CASE STUDIES</a>
                                </li>
                                <li>
                                    <a class="a1" href="javascript:;">RESOURCES</a>
                                </li>
                                <li>
                                    <a class="a1" href="/blog">BLOG</a>
                                </li>
                                <li>
                                    <a class="a1 head-button" @click="dialogInit"
                                       href="javascript:void(0)">GET
                                        PROPOSAL</a>
                                </li>
                                <div class="clear"></div>
                            </ul>
                            <div class="clear"></div>
                        </el-col>
                    </el-row>
                </el-col>
                <!--PC端导航结束-->

                <!--移动端导航开始-->
                <el-col class="moblie_head hidden-md-and-up">
                    <el-row>
                        <el-col class="block hidden-md-and-up" :xs="0" :sm="0">&nbsp;</el-col>
                        <el-col class="header-logo hidden-md-and-up" :xs="5" :sm="5">
                            <a href="javascript:;">
                                <div class="logo-img"></div>
                            </a>
                        </el-col>

                        <el-col class="hidden-sm-and-up" style="height: 82px" :xs="14">
                            <div>
                                <a class="mobile-nav-button" href="">GET PROPOSAL</a>
                            </div>
                        </el-col>

                        <el-col :xs="5" :sm="19" class="hidden-md-and-up">
                            <div class="rg">
                                <a href="javascript:;" class="a_js">
                                    <!--                            <div class="more"></div>-->
                                    <img src="https://3jbq2ynuxa-flywheel.netdna-ssl.com/wp-content/themes/klientboost/img/menu-bars-dark.svg"></a>
                            </div>
                            <div class="clear"></div>
                        </el-col>
                    </el-row>
                </el-col>
                <el-col class="a_txt hidden-md-and-up">

                    <div class="div1 a_closed"></div>

                    <div class="div3">
                        <ul>
                            <li>
                                <a href="javascript:;" class="a_closed">
                                    <img src="https://3jbq2ynuxa-flywheel.netdna-ssl.com/wp-content/themes/klientboost/img/menu-close-dark.svg"
                                         width="22">
                                </a>
                            </li>
                            <li>
                                <a :class="{'HeaderMenuItemSelect':this.ifSelect.MenuItem1classTrue==='true'}"
                                   href="/">HOME</a>
                            </li>
                            <li>
                                <a class="a_js2"
                                   :class="{'HeaderMenuItemSelect':this.ifSelect.MenuItem2classTrue==='true'}"
                                   href="javascript:;">WHAT WE DO</a>
                            </li>
                            <li>
                                <a class="a_js2"
                                   :class="{'HeaderMenuItemSelect':this.ifSelect.MenuItem3classTrue==='true'}"
                                   href="/team">TEAM</a>
                            </li>
                            <li>
                                <a class="a_js2"
                                   :class="{'HeaderMenuItemSelect':this.ifSelect.MenuItem4classTrue==='true'}"
                                   href="/caseStudies">CASE STUDIE</a>
                            </li>
                            <li>
                                <a class="a_js2"
                                   :class="{'HeaderMenuItemSelect':this.ifSelect.MenuItem5classTrue==='true'}"
                                   href="javascript:;">SRESOURCES</a>
                            </li>
                            <li>
                                <a class="a_js2"
                                   :class="{'HeaderMenuItemSelect':this.ifSelect.MenuItem6classTrue==='true'}"
                                   href="/blog">BLOG</a>
                            </li>
                            <li>
                                <a class="a_js2"
                                   :class="{'HeaderMenuItemSelect':this.ifSelect.MenuItem7classTrue==='true'}"
                                   href="/contact">CONTACT</a>
                            </li>
                            <li>
                                <a class="a1 moblie_head-button" @click="dialogInit"
                                   href="javascript:void(0)">GET
                                    PROPOSAL</a>
                            </li>
                            <div class="clear"></div>
                        </ul>
                    </div>
                </el-col>
                <!--移动端导航结束-->

            </el-row>
            <GetProposal v-if="dialogVisible" ref="getProposal"></GetProposal>
        </el-col>
    </el-row>
</template>

<script>
  import '@/assets/style/header.css'
  import GetProposal from '@/components/getProposal'

  export default {
    name: 'common-header',
    components: {
      GetProposal
    },
    props: {
      ifSelect: {
        MenuItem1classTrue: '',
        MenuItem2classTrue: '',
        MenuItem3classTrue: '',
        MenuItem4classTrue: '',
        MenuItem5classTrue: '',
        MenuItem6classTrue: '',
        MenuItem7classTrue: '',
      }
    },
    data () {
      return {
        dialogVisible:false
      }
    },
    methods:{
      dialogInit(){
        this.dialogVisible = true
        console.log("ssss")
        this.$nextTick(() => {
          this.$refs.getProposal.init()
        })
      }
    },
    mounted () {
      $(function () {
        //点击逐渐展开移动端导航
        $('.a_js').click(
          function () {
            $('.a_txt').stop(true, false).delay(0).animate({
              width: '100%',
              height: '100%'
            }, 0)
            $('.a_txt').find('.div1').stop(true, false).delay(0).animate({
              opacity: '0.9'
            }, 100)
            $('.a_txt').find('.div3').stop(true, false).delay(0).animate({
              right: '0'
            }, 100)
          }
        )
        //点击关闭，逐渐隐藏
        $('.a_closed').click(
          function () {
            $('.a_txt').stop(true, false).delay(100).animate({
              width: '0',
              height: '0'
            }, 0)
            $('.a_txt').find('.div1').stop(true, false).delay(0).animate({
              opacity: '0'
            }, 100)
            $('.a_txt').find('.div3').stop(true, false).delay(0).animate({
              right: '-50%'
            }, 100)
          })
      })
    }
  }
</script>

<style scoped>

</style>
