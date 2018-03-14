<template>
  <div class="home">
    <header class="header"></header>
    <div class="slider-container">
      <cube-slide ref="slide" :data="items">
        <cube-slide-item v-for="(item, index) in items" :key="index">
          <a :href="item.url">
            <img :src="item.image" width="100%" height="100%">
          </a>
        </cube-slide-item>
      </cube-slide>
    </div>
    <a href="javascript:" class="search-guide">
      大唐风华路
    </a>
    <nav class="home-nav">
      <a href="" class="guide-nav-a">
        <i class="icon icon-sort"></i>
        <h4 class="guide-nav-h">分类</h4>
      </a>
      <a href="" class="guide-nav-a">
        <i class="icon icon-rank"></i>
        <h4 class="guide-nav-h">排行榜</h4>
      </a>
      <a href="" class="guide-nav-a">
        <i class="icon icon-free"></i>
        <h4 class="guide-nav-h">免费</h4>
      </a>
      <a href="" class="guide-nav-a">
        <i class="icon icon-end"></i>
        <h4 class="guide-nav-h">完本</h4>
      </a>
      <a href="" class="guide-nav-a">
        <i class="icon icon-god"></i>
        <h4 class="guide-nav-h">大神</h4>
      </a>
    </nav>
    <div class="home-pure-ad">
      <a href="//qidian.gtimg.com/QDReader/?redirect=https%3A%2F%2Fitunes.apple.com%2Fcn%2Fapp%2Fqi-dian-du-shu-li-xian-ban%2Fid534174796%3Fmt%3D8" class="module-ad">
        <img src="//qidian.qpic.cn/qidian_common/349573/98630675299f399301c19529bcc02dda/0" alt="广告" class="home-pure-ad-img">
      </a>
    </div>
    <div class="module">
      <div class="module-header">
        <div class="module-header-l">
          <h3 class="module-title">热门小说</h3>
          <span class="module-title-desc" aria-hidden="true">起点编辑推荐</span>
        </div>
      </div>
      <div class="module-slide">
          <ul class="module-slide-ol" v-if="!!hot">
            <li v-for="item in hot" :key="item.bookId" class="module-slide-li">
              <a :href="item.bookId" class="module-slide-a">
                <img :src="item.imgUrl" :alt="item.bookName" class="module-slide-img">
                <figcaption class="module-slide-caption">{{item.bookName}}</figcaption>
                <p class="module-slide-author">
                  <span class="gray">{{item.author}}</span>
                </p>
              </a>
            </li>
          </ul>
      </div>
    </div>
    <div class="home-btn-line-x">
      <nav class="btn-group">
        <div class="btn-group-cell">
          <a href="/strongrec/male" class="btn-line">新书强推</a>
        </div>
        <div class="btn-group-cell">
          <a href="/sanjiang" class="btn-line">
            三江<span class="char-dot">·</span>网文新风
          </a>
        </div>
      </nav>
    </div>
    <div class="module">
      <div class="module-header">
        <div class="module-header-l">
          <h3 class="module-title">限时免费</h3>
          <time></time>
        </div>
        <div class="module-header-r">
          <a href="/free/male" class="module-header-btn">
            更多
          </a>
        </div>
      </div>
      <div class="module-slide">
        <ul class="module-slide-ol" v-if="!!free">
          <li v-for="item in free" :key="item.bookId" class="module-slide-li">
            <a :href="item.bookId" class="module-slide-a">
              <span class="corner white">
                <em>限免</em>
              </span>
              <img :src="item.imgUrl" :alt="item.bookName" class="module-slide-img">
              <figcaption class="module-slide-caption">{{item.bookName}}</figcaption>
              <p class="module-slide-author">
                <span class="gray">{{item.author}}</span>
              </p>
            </a>
          </li>
        </ul>
      </div>
    </div>
    <div class="module">
      <div class="module-header">
        <div class="module-header-l">
          <h3 class="module-title">排行榜</h3>
        </div>
        <div class="module-header-r">
          <a href="/rank/male" class="module-header-btn">
            更多
          </a>
        </div>
      </div>
      <div class="module-tab">
        <module-tab :tabs="rankTabs" @select="selectRankTab"></module-tab>
      </div>
      <div class="module-slide">
        <ul class="module-slide-ol" v-if="!!free">
          <li v-for="(item, index) in rank" :key="item.bookId" class="module-slide-li">
            <a :href="item.bookId" class="module-slide-a">
              <span class="corner-rank white">
                <em>{{'top' + (index+1)}}</em>
              </span>
              <img :src="item.imgUrl" :alt="item.bookName" class="module-slide-img">
              <figcaption class="module-slide-caption">{{item.bookName}}</figcaption>
              <p class="module-slide-author">
                <span class="gray">{{item.author}}</span>
              </p>
            </a>
          </li>
        </ul>
      </div>
    </div>
    <div class="home-pure-ad">
      <a href="http://sy.qidian.com/api/syxs/sgame/Channel.php?ishttps=false&channel=3044&type=2&gameid=200715&returnUrl=http%3A%2F%2Fsy.qidian.com%2Fapi%2Fsyxs%2Fsgame%2Fbegin.php%3Fgameid%3D200715%26ty%3D0%26partnerid%3D3044%26linkid%3D302807&qd_game_key=660x100&qd_dd_p1=7625" class="module-ad">
        <img src="//qidian.qpic.cn/qidian_common/349573/8c06e4ebf25cf7d5e3cc848fd72146a5/0" alt="广告" class="home-pure-ad-img">
      </a>
    </div>
    <div class="module">
      <div class="module-header">
        <div class="module-header-l">
          <h3 class="module-title">新书抢鲜</h3>
          <span class="module-title-desc">24小时热销新书</span>
        </div>
        <div class="module-header-r">
          <a href="/newbook/male" class="module-header-btn">
            更多
          </a>
        </div>
      </div>
      <ol class="book-ol">
        <li class="book-li" v-for="item in newest" :key="item.bookId">
          <a href="" class="book-layout">
            <img :src="item.imgUrl" :alt="item.bookName" class="book-cover">
            <div class="book-cell">
              <h4 class="book-title">{{item.bookName}}</h4>
              <p class="book-desc">{{item.desc}}</p>
              <div class="book-meta">
                <div class="book-meta-l">
                  <icon type="icon-person" color="#969ba3" size="16"/>
                  {{item.author}}
                </div>
                <div class="book-meta-r">
                <span class="tag-small-group origin-right">
                  <em class="tag-small gary">{{item.meta.type}}</em>
                  <em class="tag-small red">{{item.meta.over}}</em>
                  <em class="tag-small blue">{{item.meta.words}}</em>
                </span>
                </div>
              </div>
            </div>
          </a>
        </li>
      </ol>
    </div>
    <div class="module">
      <div class="module-header">
        <div class="module-header-l">
          <h3 class="module-title" aria-describedby="ariaDescHot">畅销完本</h3>
          <span id="ariaDescHot" class="module-title-desc" aria-hidden="true">一周热销完本书</span>
        </div>
        <div class="module-header-r">
          <a href="/bestsell/male" class="module-header-btn" data-eid="mqd_A31">更多</a>
        </div>
      </div>
      <ol class="book-ol">
        <li class="book-li" v-for="item in over" :key="item.bookId">
          <a href="" class="book-layout">
            <img :src="item.imgUrl" :alt="item.bookName" class="book-cover">
            <div class="book-cell">
              <h4 class="book-title">{{item.bookName}}</h4>
              <p class="book-desc">{{item.desc}}</p>
              <div class="book-meta">
                <div class="book-meta-l">
                  <icon type="icon-person" color="#969ba3" size="16"/>
                  {{item.author}}
                </div>
                <div class="book-meta-r">
                <span class="tag-small-group origin-right">
                  <em class="tag-small gary">{{item.meta.type}}</em>
                  <em class="tag-small red">{{item.meta.over}}</em>
                  <em class="tag-small blue">{{item.meta.words}}</em>
                </span>
                </div>
              </div>
            </div>
          </a>
        </li>
      </ol>
    </div>
  </div>
</template>

<script type="text/ecmascript-6">
  import ModuleTab from '@/base/module-tab/module-tab'
  import Icon from '@/base/icon/icon'
  export default {
    name: 'home',
    data () {
      return {
        items: [
          {
            url: 'https://m.qidian.com/book/1009961135',
            image: '//qidian.qpic.cn/qidian_common/349573/6289ee26739674f0e4c4c5279be1ffdd/0'
          },
          {
            url: 'https://m.qidian.com/book/1010839781',
            image: '//qidian.qpic.cn/qidian_common/349573/3ff2ca028ce61739a53a98479e2bb637/0'
          },
          {
            url: 'https://m.qidian.com/book/1010426071',
            image: '//qidian.qpic.cn/qidian_common/349573/87f20e284b336ba82713379b4cb27a1c/0'
          },
          {
            url: 'https://m.qidian.com/book/3491527',
            image: '//qidian.qpic.cn/qidian_common/349573/e1901e3035c53f14c87118d455cdb3d7/0'
          }
        ],
        hot: [
          {
            bookId: '1011029438',
            imgUrl: '//qidian.qpic.cn/qdbimg/349573/1011029438/150',
            bookName: '吹神',
            author: '辰机唐红豆'
          },
          {
            bookId: '1004879785',
            imgUrl: '//qidian.qpic.cn/qdbimg/349573/1004879785/150',
            bookName: '仙药供应商',
            author: '糖醋于'
          },
          {
            bookId: '1010635438',
            imgUrl: '//qidian.qpic.cn/qdbimg/349573/1010635438/150',
            bookName: '信仰大爆炸',
            author: '夜色静悄悄'
          },
          {
            bookId: '1011097497',
            imgUrl: '//qidian.qpic.cn/qdbimg/349573/1011097497/150',
            bookName: '秦吏',
            author: '七月新番'
          },
          {
            bookId: '1009758360',
            imgUrl: '//qidian.qpic.cn/qdbimg/349573/1009758360/150',
            bookName: '山海画妖师',
            author: '苍知'
          },
          {
            bookId: '1010468795',
            imgUrl: '//qidian.qpic.cn/qdbimg/349573/1010468795/150',
            bookName: '飞剑问道',
            author: '我吃西红柿'
          },
          {
            bookId: '1010957891',
            imgUrl: '//qidian.qpic.cn/qdbimg/349573/1010957891/150',
            bookName: '浴血兵锋',
            author: '丑牛1985'
          }
        ],
        free: [
          {
            bookId: '1004834723',
            imgUrl: '//qidian.qpic.cn/qdbimg/349573/1004834723/150',
            bookName: '通天仙路',
            author: '苍天白鹤'
          },
          {
            bookId: '1009924835',
            imgUrl: '//qidian.qpic.cn/qdbimg/349573/1009924835/150',
            bookName: '钻石王牌之投手归来',
            author: '飞熊骑士'
          },
          {
            bookId: '1010042953',
            imgUrl: '//qidian.qpic.cn/qdbimg/349573/1010042953/150',
            bookName: '王者荣耀直播穿越系统',
            author: '疯狂的石头怪'
          },
          {
            bookId: '1010056141',
            imgUrl: '//qidian.qpic.cn/qdbimg/349573/1010056141/150',
            bookName: '东晋北府一丘八',
            author: '指云笑天道1'
          },
          {
            bookId: '1009359781',
            imgUrl: '//qidian.qpic.cn/qdbimg/349573/1009359781/150',
            bookName: '大明军工帝国',
            author: '星辰玖'
          },
          {
            bookId: '1009636670',
            imgUrl: '//qidian.qpic.cn/qdbimg/349573/1009636670/150',
            bookName: '恐怖短信',
            author: '秋水'
          }
        ],
        rank: [
          {
            bookId: '1010191960',
            imgUrl: '//qidian.qpic.cn/qdbimg/349573/1010191960/150',
            bookName: '大王饶命',
            author: '会说话的肘子'
          },
          {
            bookId: '1004608738',
            imgUrl: '//qidian.qpic.cn/qdbimg/349573/1004608738/150',
            bookName: '圣墟',
            author: '辰东'
          },
          {
            bookId: '1009704712',
            imgUrl: '//qidian.qpic.cn/qdbimg/349573/1009704712/150',
            bookName: '牧神记',
            author: '宅猪'
          },
          {
            bookId: '3602691',
            imgUrl: '//qidian.qpic.cn/qdbimg/349573/3602691/150',
            bookName: '修真聊天群',
            author: '圣骑士的传说'
          },
          {
            bookId: '1004179514',
            imgUrl: '//qidian.qpic.cn/qdbimg/349573/1004179514/150',
            bookName: '天道图书馆',
            author: '横扫天涯'
          },
          {
            bookId: '1005236478',
            imgUrl: '//qidian.qpic.cn/qdbimg/349573/1005236478/150',
            bookName: '道君',
            author: '跃千愁'
          },
          {
            bookId: '1010734492',
            imgUrl: '//qidian.qpic.cn/qdbimg/349573/1010734492/150',
            bookName: '凡人修仙之仙界篇',
            author: '忘语'
          },
          {
            bookId: '1003692682',
            imgUrl: '//qidian.qpic.cn/qdbimg/349573/1003692682/150',
            bookName: '超级神基因',
            author: '十二翼黑暗炽天使'
          },
          {
            bookId: '1010468795',
            imgUrl: '//qidian.qpic.cn/qdbimg/349573/1010468795/150',
            bookName: '飞剑问道',
            author: '我吃西红柿'
          },
          {
            bookId: '1010426071',
            imgUrl: '//qidian.qpic.cn/qdbimg/349573/1010426071/150',
            bookName: '诸界末日在线',
            author: '烟火成城'
          }
        ],
        newest: [
          {
            bookId: '1010734492',
            imgUrl: '//qidian.qpic.cn/qdbimg/349573/1010734492/150',
            bookName: '凡人修仙之仙界篇',
            desc: '凡人修仙，风云再起时空穿梭，轮回逆转金仙太乙，大罗道祖三千大道，法则至尊《凡人修仙传》仙界篇，一个韩立叱咤仙界的故事，一个凡人小子修仙的不灭传说。特说明下，没有看过前传的书友，并不影响本书的阅读体验，但感兴趣的书友，也可以先去看看《凡人修仙传》，再来看本书哦。',
            author: '忘语',
            meta: {
              type: '仙侠',
              over: '连载中',
              words: '56.99万字'
            }
          },
          {
            bookId: '1010287217',
            imgUrl: '//qidian.qpic.cn/qdbimg/349573/1010287217/150',
            bookName: '最终深渊',
            desc: '人类有幻想，所以诞生了电影、动漫、小说...，但人类不是宇宙中唯一拥有幻想的生命，当全宇宙的幻想意识凝聚在一起的时候，一扇上帝之门就此诞生。这里有浩瀚星空，亦有血与歌的杀戮，光怪陆离的新世界在眼前展开，穿梭在万千任务世界之中，唯有实力才是打开真理之门的钥匙（qq群178401496）',
            author: '一条咸鱼而已',
            meta: {
              type: '科幻',
              over: '连载中',
              words: '74.18万字'
            }
          },
          {
            bookId: '1010839781',
            imgUrl: '//qidian.qpic.cn/qdbimg/349573/1010839781/150',
            bookName: '太监武帝',
            desc: '穿越玄幻版中国古代，成为阉党一小太监。太监养成系统启动，目标：称霸阉党，入主东厂；恢复雄风，迎娶未来女皇。杜变发现在梦境中能够预知即将发生之事，躲开灾祸。而且在梦境中修炼学习，时间变慢十倍，脑域开发提升十倍。从此，他要无敌了！',
            author: '沉默的糕点',
            meta: {
              type: '玄幻',
              over: '连载中',
              words: '117.12万字'
            }
          }
        ],
        over: [
          {
            bookId: '1115277',
            imgUrl: '//qidian.qpic.cn/qdbimg/349573/1115277/150',
            bookName: '斗罗大陆',
            desc: '唐门外门弟子唐三，因偷学内门绝学为唐门所不容，跳崖明志时却发现没有死，反而以另外一个身份来到了另一个世界，一个属于武魂的世界，名叫斗罗大陆。这里没有魔法，没有斗气，没有武术，却有神',
            author: '唐家三少',
            meta: {
              type: '玄幻',
              over: '完本',
              words: '272.67万字'
            }
          },
          {
            bookId: '107580',
            imgUrl: '//qidian.qpic.cn/qdbimg/349573/107580/150',
            bookName: '凡人修仙传',
            desc: '一个普通山村小子，偶然下进入到当地江湖小门派，成了一名记名弟子。他以这样身份，如何在门派中立足,如何以平庸的资质进入到修仙者的行列，从而笑傲三界之中！续篇《凡人修仙之仙界篇》已经在',
            author: '忘语',
            meta: {
              type: '仙侠',
              over: '完本',
              words: '744.45万字'
            }
          },
          {
            bookId: '2413595',
            imgUrl: '//qidian.qpic.cn/qdbimg/349573/2413595/150',
            bookName: '唐砖',
            desc: '梦回长安，鲜血浸染了玄武门，太极宫的深处只有数不尽的悲哀，民为水，君为舟，的朗朗之音犹在长安大地回绕，异族的铁蹄却再一次踏破了玉门关，此恨何及？坟墓里的李世民眼见子民涂炭，该发出怎',
            author: '孑与2',
            meta: {
              type: '历史',
              over: '完本',
              words: '445.28万字'
            }
          }
        ],
        rankTabs: ['热销榜', '风云榜', '签约榜', '推荐榜']
      }
    },
    methods: {
      selectRankTab (index) {
        const sellRank = [
          {
            bookId: '1010191960',
            imgUrl: '//qidian.qpic.cn/qdbimg/349573/1010191960/150',
            bookName: '大王饶命',
            author: '会说话的肘子'
          },
          {
            bookId: '1004608738',
            imgUrl: '//qidian.qpic.cn/qdbimg/349573/1004608738/150',
            bookName: '圣墟',
            author: '辰东'
          },
          {
            bookId: '1009704712',
            imgUrl: '//qidian.qpic.cn/qdbimg/349573/1009704712/150',
            bookName: '牧神记',
            author: '宅猪'
          },
          {
            bookId: '3602691',
            imgUrl: '//qidian.qpic.cn/qdbimg/349573/3602691/150',
            bookName: '修真聊天群',
            author: '圣骑士的传说'
          },
          {
            bookId: '1004179514',
            imgUrl: '//qidian.qpic.cn/qdbimg/349573/1004179514/150',
            bookName: '天道图书馆',
            author: '横扫天涯'
          },
          {
            bookId: '1005236478',
            imgUrl: '//qidian.qpic.cn/qdbimg/349573/1005236478/150',
            bookName: '道君',
            author: '跃千愁'
          },
          {
            bookId: '1010734492',
            imgUrl: '//qidian.qpic.cn/qdbimg/349573/1010734492/150',
            bookName: '凡人修仙之仙界篇',
            author: '忘语'
          },
          {
            bookId: '1003692682',
            imgUrl: '//qidian.qpic.cn/qdbimg/349573/1003692682/150',
            bookName: '超级神基因',
            author: '十二翼黑暗炽天使'
          },
          {
            bookId: '1010468795',
            imgUrl: '//qidian.qpic.cn/qdbimg/349573/1010468795/150',
            bookName: '飞剑问道',
            author: '我吃西红柿'
          },
          {
            bookId: '1010426071',
            imgUrl: '//qidian.qpic.cn/qdbimg/349573/1010426071/150',
            bookName: '诸界末日在线',
            author: '烟火成城'
          }
        ]
        const trendRank = [
          {
            bookId: '1010399782',
            imgUrl: '//qidian.qpic.cn/qdbimg/349573/1010399782/150',
            bookName: '太初',
            author: '高楼大厦'
          },
          {
            bookId: '1011058239',
            imgUrl: '//qidian.qpic.cn/qdbimg/349573/1011058239/150',
            bookName: '伏天氏',
            author: '净无痕'
          },
          {
            bookId: '1011029438',
            imgUrl: '//qidian.qpic.cn/qdbimg/349573/1011029438/150',
            bookName: '吹神',
            author: '辰机唐红豆'
          },
          {
            bookId: '3602691',
            imgUrl: '//qidian.qpic.cn/qdbimg/349573/3602691/150',
            bookName: '修真聊天群',
            author: '圣骑士的传说'
          },
          {
            bookId: '1004179514',
            imgUrl: '//qidian.qpic.cn/qdbimg/349573/1004179514/150',
            bookName: '天道图书馆',
            author: '横扫天涯'
          },
          {
            bookId: '1005236478',
            imgUrl: '//qidian.qpic.cn/qdbimg/349573/1005236478/150',
            bookName: '道君',
            author: '跃千愁'
          },
          {
            bookId: '1010734492',
            imgUrl: '//qidian.qpic.cn/qdbimg/349573/1010734492/150',
            bookName: '凡人修仙之仙界篇',
            author: '忘语'
          },
          {
            bookId: '1003692682',
            imgUrl: '//qidian.qpic.cn/qdbimg/349573/1003692682/150',
            bookName: '超级神基因',
            author: '十二翼黑暗炽天使'
          },
          {
            bookId: '1010468795',
            imgUrl: '//qidian.qpic.cn/qdbimg/349573/1010468795/150',
            bookName: '飞剑问道',
            author: '我吃西红柿'
          },
          {
            bookId: '1010426071',
            imgUrl: '//qidian.qpic.cn/qdbimg/349573/1010426071/150',
            bookName: '诸界末日在线',
            author: '烟火成城'
          }
        ]
        const contractRank = [
          {
            bookId: '1011322692',
            imgUrl: '//qidian.qpic.cn/qdbimg/349573/1011322692/150',
            bookName: '无限福利神豪',
            author: '我狙个栗子'
          },
          {
            bookId: '1011311930',
            imgUrl: '//qidian.qpic.cn/qdbimg/349573/1011311930/150',
            bookName: '重生之作死大宗师',
            author: '碧云桃子'
          },
          {
            bookId: '1010744110',
            imgUrl: '//qidian.qpic.cn/qdbimg/349573/1010744110/150',
            bookName: '纯情大明星',
            author: '冒牌大叔'
          },
          {
            bookId: '3602691',
            imgUrl: '//qidian.qpic.cn/qdbimg/349573/3602691/150',
            bookName: '修真聊天群',
            author: '圣骑士的传说'
          },
          {
            bookId: '1004179514',
            imgUrl: '//qidian.qpic.cn/qdbimg/349573/1004179514/150',
            bookName: '天道图书馆',
            author: '横扫天涯'
          },
          {
            bookId: '1005236478',
            imgUrl: '//qidian.qpic.cn/qdbimg/349573/1005236478/150',
            bookName: '道君',
            author: '跃千愁'
          },
          {
            bookId: '1010734492',
            imgUrl: '//qidian.qpic.cn/qdbimg/349573/1010734492/150',
            bookName: '凡人修仙之仙界篇',
            author: '忘语'
          },
          {
            bookId: '1003692682',
            imgUrl: '//qidian.qpic.cn/qdbimg/349573/1003692682/150',
            bookName: '超级神基因',
            author: '十二翼黑暗炽天使'
          },
          {
            bookId: '1010468795',
            imgUrl: '//qidian.qpic.cn/qdbimg/349573/1010468795/150',
            bookName: '飞剑问道',
            author: '我吃西红柿'
          },
          {
            bookId: '1010426071',
            imgUrl: '//qidian.qpic.cn/qdbimg/349573/1010426071/150',
            bookName: '诸界末日在线',
            author: '烟火成城'
          }
        ]
        const recommendRank = [
          {
            bookId: '2510964',
            imgUrl: '//qidian.qpic.cn/qdbimg/349573/2510964/150',
            bookName: '龙皇武神',
            author: '步征'
          },
          {
            bookId: '1010468795',
            imgUrl: '//qidian.qpic.cn/qdbimg/349573/1010468795/150',
            bookName: '飞剑问道',
            author: '我吃西红柿'
          },
          {
            bookId: '1010399782',
            imgUrl: '//qidian.qpic.cn/qdbimg/349573/1010399782/150',
            bookName: '太初',
            author: '高楼大厦'
          },
          {
            bookId: '3602691',
            imgUrl: '//qidian.qpic.cn/qdbimg/349573/3602691/150',
            bookName: '修真聊天群',
            author: '圣骑士的传说'
          },
          {
            bookId: '1004179514',
            imgUrl: '//qidian.qpic.cn/qdbimg/349573/1004179514/150',
            bookName: '天道图书馆',
            author: '横扫天涯'
          },
          {
            bookId: '1005236478',
            imgUrl: '//qidian.qpic.cn/qdbimg/349573/1005236478/150',
            bookName: '道君',
            author: '跃千愁'
          },
          {
            bookId: '1010734492',
            imgUrl: '//qidian.qpic.cn/qdbimg/349573/1010734492/150',
            bookName: '凡人修仙之仙界篇',
            author: '忘语'
          },
          {
            bookId: '1003692682',
            imgUrl: '//qidian.qpic.cn/qdbimg/349573/1003692682/150',
            bookName: '超级神基因',
            author: '十二翼黑暗炽天使'
          },
          {
            bookId: '1011322692',
            imgUrl: '//qidian.qpic.cn/qdbimg/349573/1011322692/150',
            bookName: '无限福利神豪',
            author: '我狙个栗子'
          },
          {
            bookId: '1010426071',
            imgUrl: '//qidian.qpic.cn/qdbimg/349573/1010426071/150',
            bookName: '诸界末日在线',
            author: '烟火成城'
          }
        ]
        if (index === 0) {
          this.rank = sellRank
        } else if (index === 1) {
          this.rank = trendRank
        } else if (index === 2) {
          this.rank = contractRank
        } else if (index === 3) {
          this.rank = recommendRank
        }
      }
    },
    components: {
      ModuleTab,
      Icon
    }
  }
</script>

<style scoped lang="stylus">
  .home
    background-color: #f6f7f9
    .header
      position: relative
      box-sizing: border-box
      height: 2.75rem
      padding-top: .7875rem
      padding-bottom: .625rem
    .slider-container
      position: relative
      overflow: hidden
      height: calc(.314 * (100vw - 1.5rem))
      margin: 0 .75rem
    .search-guide
      font-size: .8125rem
      line-height: 2rem
      display: block
      margin: .375rem .75rem
      text-align: center
      color: #969ba3
      border-radius: .25rem
      background-color: #ffffff
    .home-nav
      display: flex
      justify-content: space-between
      margin: .375rem 0
      padding: .75rem .625rem
      background-color: #ffffff
      .guide-nav-a
        display: block
        position: relative
        font-size: .75rem
        width: 3.5rem
        height: 3.625rem
        text-align: center
        .icon
          position: absolute
          right: 0
          bottom: 1.625rem
          left: 0
          margin: auto
        .icon-sort
          background-image: url("https://qidian.gtimg.com/qdm/icon/common/sprite.b2b30.png")
          background-position: -63px -28px
          width: 24px
          height: 24px
        .icon-rank
          background-image: url("https://qidian.gtimg.com/qdm/icon/common/sprite.b2b30.png")
          background-position:0 0
          width: 27px
          height: 26px
        .icon-free
          background-image: url("https://qidian.gtimg.com/qdm/icon/common/sprite.b2b30.png")
          background-position:0 -30px
          width: 26px
          height: 26px
        .icon-end
          background-image: url("https://qidian.gtimg.com/qdm/icon/common/sprite.b2b30.png")
          background-position:0 -60px
          width: 20px
          height: 27px
        .icon-god
          background-image: url("https://qidian.gtimg.com/qdm/icon/common/sprite.b2b30.png")
          background-position:-30px -30px
          width: 26px
          height: 26px
        @media (-webkit-min-device-pixel-ratio: 2), (min-resolution: 192dpi)
          .icon-sort, .icon-rank, .icon-free, .icon-end, .icon-god
            background-image: url("https://qidian.gtimg.com/qdm/icon/common/sprite@2x.f5569.png")
            background-size: 87px 87px
        .guide-nav-h
          position: absolute
          right: 0
          bottom: .1875rem
          left: 0
    .home-pure-ad
      padding: 0 1rem
      .module-ad
        position: relative
        display: block
        overflow: hidden
        margin: .75rem 0
        padding: 7.575757% 50%
        img:only-child
          position: absolute
          top: 0
          left: 0
          width: 100%
          height: 100%
    .module
      margin: .75rem 0
      background-color: #ffffff
      .module-header
        height:1.75rem
        padding:0 1rem
        border-top:1rem solid transparent
        .module-header-l
          float: left
          .module-title
            font-weight: 400
            display: inline
            color: #33373d
          .module-title-desc
            font-size: .8125rem
            margin-left: .5rem
            color: #969ba3
        .module-header-r
          position: relative
          float: right
          min-width: 4rem
          .module-header-btn
            font-size: .875rem
            line-height: 1.5rem
            position: absolute
            top: -.5rem
            right: -.75rem
            padding: .5rem .5rem .5rem .75rem
            white-space: nowrap
            color: #969ba3
      .module-tab
        margin: .4375rem 1rem
      .book-ol
        .book-li
          .book-layout
            position: relative
            display: block
            overflow: hidden
            padding: 1rem
            transition: padding-left .15s
            .book-cover
              font-size: 0
              float: left
              width: 4.125rem
              height: 5.5rem
              margin-right: .5rem
              box-shadow: 0 1px 3px rgba(0,0,0,.3)
            .book-cell
              overflow: hidden
              .book-title
                line-height: 1.4
                overflow: hidden
                white-space:nowrap
                text-overflow: ellipsis
              .book-desc
                line-height: 1.1875rem
                display: box
                height: 2.25rem
                box-orient: vertical
                line-clamp: 2
                font-size: .875rem
                overflow: hidden
                margin: .375rem 0
                color: #969ba3
                text-overflow: ellipsis
              .book-meta
                font-size: .75rem
                overflow: hidden
                .book-meta-l
                  float: left
                  .book-author
                    font-size: .8125rem
                    display: block
                    overflow: hidden
                    max-width: calc(100vw - 2rem - (176rem / 16))
                    white-space: nowrap
                    text-overflow: ellipsis
                    color: #969ba3
                .book-meta-r
                  position: relative
                  .tag-small-group
                    position: absolute
                    top: -.375rem
                    right: 0
                    white-space: nowrap
                    transform: scale(.5)
                  .origin-right
                    transform-origin: right center
                    .tag-small
                      font-size: 1.25rem
                      line-height: 1.5
                      display: inline-block
                      margin: 0 .15rem
                      padding:0 .25rem
                      vertical-align: bottom
                      font-style: normal
      .module-slide
        .module-slide-ol
          position: relative
          overflow-x: auto
          overflow-y: hidden
          min-height: 10.75rem
          padding-left: .5rem
          white-space: nowrap
          &::-webkit-scrollbar
            display: none
          .module-slide-li
            display: inline-block
            vertical-align: top
            &:nth-child(1)
              .corner-rank
                em
                  background-color: #ed424b!important;
            &:nth-child(2)
              .corner-rank
                em
                  background-color: #f0643a!important;
            &:nth-child(3)
              .corner-rank
                em
                  background-color: #f0c53a!important;
            .module-slide-a
              display: block
              width: 4.125rem
              padding: .75rem .5rem .5rem
              .white
                color: #ffffff
              .corner
                font-size: 10px
                position: absolute
                overflow: hidden
                width: 30px
                height: 30px
                text-align: center
                em
                  font-size: 10px;
                  line-height: 11px;
                  position: absolute;
                  right: -12px;
                  bottom: 0;
                  left: 0;
                  padding-top: 1px;
                  transform: rotate(-45deg);
                  transform-origin: left bottom;
                  color: inherit;
                  background-color: #4284ed;
              .corner-rank
                font-size: 10px
                position: absolute
                overflow: hidden
                width: 30px
                height: 30px
                text-align: center
                em
                  font-size: 10px;
                  line-height: 11px;
                  position: absolute;
                  right: -12px;
                  bottom: 0;
                  left: 0;
                  padding-top: 1px;
                  transform: rotate(-45deg);
                  transform-origin: left bottom;
                  color: inherit;
                  background-color: #969ba3;
              .module-slide-img
                display: block
                width: inherit
                height: 5.5rem
                box-shadow: 0 1px 3px rgba(0,0,0,.3)
              .module-slide-caption
                font-size: .8125rem
                line-height: 1.25
                overflow: hidden
                max-height: 2.125rem
                margin: .5rem 0 0.125rem
                color: rgb(51,55,61)
              .module-slide-author
                font-size: .75rem
                overflow: hidden
                white-space: nowrap
                text-overflow: ellipsis
                color: #969ba3
                .gray
                  color: #969ba3
    .home-btn-line-x
      margin: 1rem
      .btn-group
        display: table
        width: 100%
        margin-left: auto
        margin-right: auto
        table-layout: fixed
        .btn-group-cell
          font-size: 100%
          font-weight: 400
          display: table-cell
          .btn-line
            display: block
            margin: 0 .5625rem
            color: #ed424b
            font-size: .8125rem
            line-height: 1.6875rem
            padding: 0 .625rem
            text-align: center
            border:1px solid
            border-radius: 99px
</style>
