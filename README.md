# hexo-butterfly-swiper-ihao

给`hexo-theme-butterfly`添加 [首页轮播图](https://akilar.top/posts/8e1264d1/)

# 安装

1. 安装插件,在博客根目录`[Blogroot]`下打开终端，运行以下指令：
  ```bash
  npm install hexo-butterfly-swiper-ihao --save
  ```

2. 添加配置信息，以下为写法示例
  在站点配置文件`_config.yml`或者主题配置文件`_config.butterfly.yml`中添加

  ```yml
    swiper:
      enable: true # 开关
      randomenable: true # 人潮汹涌开关
      priority: 5 #过滤器优先权
      enable_page: / # 应用页面
      timemode: date #date/updated
      layout: # 挂载容器类型
        type: id
        name: home_top
        index: 1
      category:
        - name: 必看精选
          path: /categories/必看精选/
          shadow: var(--ihao-shadow-blue)
          class: blue
          icon: fas fa-dove
        - name: 大学
          path: /categories/大学/
          shadow: var(--ihao-shadow-red)
          class: red
          icon: fas fa-burn
        - name: 生活
          path: /categories/生活/
          shadow: var(--ihao-shadow-green)
          class: green
          icon: fas fa-book
      default_descr: 再怎么看我也不知道怎么描述它的啦！
      swiper_css: https://cdn.cbd.int/hexo-butterfly-swiper-ihao/lib/swiper.min.css #swiper css依赖
      swiper_js: https://npm.elemecdn.com/ihao-blog@1.0.0/js/swiper.min.js #swiper js依赖 #swiper js依赖
      custom_css: https://cdn.cbd.int/hexo-butterfly-swiper-ihao/lib/swiperstyle.css # 适配主题样式补丁
      custom_js: https://cdn.cbd.int/hexo-butterfly-swiper-ihao/lib/swiper_init.js # swiper初始化方法
      gsap_js: https://lf26-cdn-tos.bytecdntp.com/cdn/expire-1-M/gsap/3.9.1/gsap.min.js
      people_js: https://npm.elemecdn.com/hexo-butterfly-swiper-ihao/lib/people.min.js
      categorygroup_css: https://cdn.cbd.int/hexo-butterfly-swiper-ihao/lib/categoryGroup.css
  ```
3. 参数释义

  |参数|备选值/类型|释义|
  |:--|:--|:--|
  |priority|number|【可选】过滤器优先级，数值越小，执行越早，默认为10，选填|
  |enable|true/false|【必选】控制开关|
  |randomenable|true/false|【必选】人潮汹涌控制开关|
  |enable_page|path/all|【可选】填写想要应用的页面的相对路径（即路由地址）,如根目录就填'/',分类页面就填'/categories/'。若要应用于所有页面，就填'all'，默认为all|
  |exclude|path|【可选】填写想要屏蔽的页面，可以多个。仅当enable_page为'all'时生效。写法见示例。原理是将屏蔽项的内容逐个放到当前路径去匹配，若当前路径包含任一屏蔽项，则不会挂载。|
  |timemode|date/updated|【可选】时间显示，date为显示创建日期，updated为显示更新日期,默认为date|
  |layout.type|id/class|【可选】挂载容器类型，填写id或class，不填则默认为id|
  |layout.name|text|【必选】挂载容器名称|
  |layout.index|0和正整数|【可选】前提是layout.type为class，因为同一页面可能有多个class，此项用来确认究竟排在第几个顺位|
  |error_img|url|封面图片加载失败时的替换图片|
  |insertposition|text|'beforebegin'：元素自身的前面。'afterbegin'：插入元素内部的第一个子节点之前。'beforeend'：插入元素内部的最后一个子节点之后。'afterend'：插入元素自身的后面。|
  |default_descr|text|【可选】默认文章描述|
  |swiper_css|url|【可选】自定义的swiper依赖项css链接|
  |swiper_js|url|【可选】自定义的swiper依赖项加js链接|
  |custom_css|url|【可选】适配主题样式补丁|
  |custom_js|url|【可选】swiper初始化方法|
  |gsap_js|url|【可选】gsap_js依赖|
  |people_js|url|【可选】随机逛逛js|
  |categorygroup_css|url|【可选】分类类别css|

4. 使用方法
  在文章的`front_matter`中添加`swiper_index`配置项控制轮播图, `top_group_index`控制右侧文章磁贴。
  ```markdown
  ---
  title: 文章标题
  date: 创建日期
  updated: 更新日期
  cover: 文章封面
  description: 文章描述
  swiper_index: 1 #置顶轮播图顺序，需填非负整数，数字越大越靠前
  top_group_index: 1 #右侧磁帖顺序，需填非负整数，数字越大越靠前
  ---
  ```
5. 另外你可能没有该挂载元素需要自行挂载元素，添加自己的css以进行适配, 如我的挂载元素为`home_top`, 我额外的css为
```css
#home_top {
  margin: 1rem auto 0;
  padding: 0px 15px;
  max-width: 1450px;
  width: 100%;
}
```
