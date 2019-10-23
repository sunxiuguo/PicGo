<template lang='pug'>
  #app(v-cloak)
    #header
      .mask
      img.logo(src="~icons/icon.svg", alt="VisualClipboard")
      h1.title VisualClipboard
      h2.desc 优雅的剪贴板可视化管理
      button.download(@click="goLink('https://github.com/sunxiuguo')") 免费下载
      button.download(@click="goLink('https://github.com/sunxiuguo')") 查看文档
      h3.desc
        | 支持macOS,Windows
    #container.container-fluid
      .row.ex-width
        img.gallery.col-xs-10.col-xs-offset-1.col-md-offset-2.col-md-8(src="https://cdn.zhusun.club/image/clipboard/12.png")
      .row.ex-width.display-list
        .display-list__item(v-for="(item, index) in itemList" :key="index" :class="{ 'o-item': index % 2 !== 0 }")
          .col-xs-10.col-xs-offset-1.col-md-7.col-md-offset-0
            img(:src="item.url")
          .col-xs-10.col-xs-offset-1.col-md-5.col-md-offset-0.display-list__content
            .display-list__title {{ item.title }} 
            .display-list__desc {{ item.desc }}
      .row.ex-width.info
        .col-xs-10.col-xs-offset-1
          | &copy;2019 - {{ year }} #[a(href="https://github.com/sunxiuguo" target="_blank") sunxiuguo]
</template>
<script>
export default {
  data () {
    return {
      year: new Date().getFullYear(),
      itemList: [
        {
          url: 'https://cdn.zhusun.club/image/clipboard/1.png',
          title: '优雅设计',
          desc: '支持复制多种格式，保留复制内容的所有样式，内容丰富，内容过多时可以滚动查看，方便查找您的剪贴板记录。'
        },
        {
          url: 'https://cdn.zhusun.club/image/clipboard/4.png',
          title: '元模块',
          desc: '每个剪贴板记录的元模块，包含顶部tabbar，中间的内容区域展示原格式内容，下方记录您复制此条内容的时间，也给您提供了复制按钮，方便再次复制。'
        },
        {
          url: 'https://cdn.zhusun.club/image/clipboard/5.png',
          title: '图片记录',
          desc: '支持记录剪贴板图片记录，无论是截屏还是复制图片，都会记录在我们的剪贴板里，列表展示图片缩略图，方便快速查找。'
        },
        {
          url: 'https://cdn.zhusun.club/image/clipboard/6.png',
          title: '大图预览',
          desc: '点击列表缩略图，可以预览更高画质的图片记录。'
        },
        {
          url: 'https://cdn.zhusun.club/image/clipboard/3.png',
          title: '关键字搜索',
          desc: '右上角预留了关键字搜索栏，可以在此输入关键字，方便快捷的搜索到目标记录。'
        }
      ]
    }
  },
  methods: {
    goLink (link) {
      window.open(link, '_blank')
    }
  }
}
</script>
<style lang='stylus'>
[v-cloak]
  display none
*
  box-sizing border-box
body,
html,
h1
  margin 0
  padding 0
  font-family "Source Sans Pro","Helvetica Neue","PingFang SC","Hiragino Sans GB","Microsoft YaHei","微软雅黑",Arial,sans-serif  
html
    background #f5f5f5
#app
  position relative
.mask
  position absolute
  width 100%
  height 100vh
  top 0
  left 0
  background rgba(0,0,0, 0.7)
  z-index -1
#header
  height 100vh
  width 100%
  background-image url("https://cdn.zhusun.club/image/clipboard/backg.jpeg")
  background-attachment fixed
  background-size cover
  background-position center
  text-align center
  padding 15vh
  position relative
  z-index 2
  .logo
    width 120px
  .title
    color #4BA2E2
    font-size 36px
    font-weight 300
    margin 10px auto
    text-align center
    small
      margin-left 10px
      font-size 14px
  .desc
    font-weight 400
    margin 20px auto 10px
    color #ddd
    a
      text-decoration none
      color #4BA2E2
  .download
    display inline-block
    line-height 1
    white-space nowrap
    cursor pointer
    background transparent
    border 1px solid #d8dce5
    color #ddd
    -webkit-appearance none
    text-align center
    box-sizing border-box
    outline none
    margin 20px 12px
    transition .1s
    font-weight 500
    user-select none
    padding 12px 20px
    font-size 14px
    border-radius 20px
    padding 12px 23px
    transition .2s all ease-in-out
    &:hover
      background #ddd
      color rgba(0,0,0, 0.7)
#container
  position relative
  text-align center
  margin-top -10vh
  z-index 3
  .gallery
    margin-bottom 60px
    cursor pointer
    transition all .2s ease-in-out
    &:hover
      transform scale(1.05)
  .display-list
    &__item
      padding 48px
      text-align left
      background #2E2E2E
      overflow hidden
      &.o-item
        background #f5f5f5
        .display-list__desc
          color #2E2E2E
      img
        width 100%
        cursor pointer
        transition all .2s ease-in-out
        &:hover
          transform scale(1.05)
    &__content
      padding-top 120px
    &__title
      color #4BA2E2
      font-size 50px
    &__desc
      color #fff
      margin-top 20px
  .info
    padding 24px 0
    background #2E2E2E
    color #fff
    a
      text-decoration none
      color #fff
@media (max-width: 768px)
  #header
    padding 10vh
  #container
    .display-list
      &__item
        padding 24px 12px
      &__content
        padding-top 30px
      &__title
        font-size 25px
      &__desc
        margin-top 12px
</style>