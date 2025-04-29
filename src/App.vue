<script setup>
import { onMounted, reactive } from 'vue'
import StarTrails from './components/StarTrails.vue'
import { updateYear } from './JavaScript/updateYear.js'
import { smoothScroll } from './JavaScript/smoothScroll.js'

const data = reactive({
  titleList: [
  '要有勇气去追随你的心和直觉——它们知道你想成为什么',
  '人生苦短，不要浪费时间在别人的期待里',
  '往日不悔，未来可期',
  '脚步丈量世界时，山海皆为壮美注脚',
  '每粒尘埃都有方向，每阵风都藏着远方',
  '你只管努力，剩下的交给时间',
  'Success is not final<br/>Failure is not fatal',
  '夢を見続ける者だけが<br/>未来を掴む',
  '把自己当傻瓜，不懂就问，你会学到更多',
  '星光不问赶路人<br/>时光不负有心人',
  '心有所念<br/>方能坚持向前',
  '保持独立<br/>不被外界所左右',
  '以赤子之心穿越迷雾，归来仍是少年模样',
  'Don’t watch the clock;<br/>do what it does. Keep going.',
  '过去无法重写<br/>却让我更加坚强',
  '一个人为什么要努力？<br/>因为梦想值得拼尽全力',
],
  navLinks: [/* {
    name: 'Blog',
    link: 'https://blog.hanahime.online',
  }, */ {
    name: 'Index',
    link: 'https://LhyYBMQ520.github.io',
  }],

  myProjects: [{
    name: 'Index',
    description: '个人简介、主页、引导页',
    link: 'https://github.com/LhyYBMQ520/LhyYBMQ520.github.io',
  }, /* {
    name: 'Blog',
    description: '个人博客，学习&随笔',
    link: 'https://blog.hanahime.online',
  }, */ {
    name: 'undefined',
    description: '喵喵喵~ 暂时没有别的东西 wv',
    link: './',
  }],

  socialLinks: [{
    icon: '<i i-ant-design-github-outlined />',
    link: 'https://github.com/LhyYBMQ520',
    label: 'Github',
  }, {
    icon: '<i i-ant-design-x-outlined />',
    link: 'https://twitter.com/LhyYbmq',
    label: 'Twitter',
  }, /* {
    icon: '<i i-ant-design-youtube-outlined />',
    link: 'https://youtube.com/@userId',
    label: 'YouTube',
  }, */ {
    icon: '<i i-ant-design-bilibili-outlined />',
    link: 'https://space.bilibili.com/1211287493/',
    label: 'Bilibili',
  }],
})

onMounted(() => {
  // 背景固定
  window.addEventListener('scroll', () => {
    const bg = document.getElementById('background')
    const scrollTop = window.scrollY
    if (scrollTop > 0.7 * window.innerHeight)
      bg.classList.add('fixed')
    else
      bg.classList.remove('fixed')
  })
  // 页脚Copyright时间
  updateYear()
})
</script>

<template>
  <!-- 导航 -->
  <nav absolute fixed bottom-4 left-4 z-20>
    <div v-for="(item, index) in data.navLinks" :key="index" my-6 text-3 text-white wv>
      <a :href="item.link" opacity-75 text-white tracking-widest hover:opacity-100>
        {{ item.name }}
      </a>
    </div>
  </nav>

  <!-- 主体 -->
  <main bg-transparent absolute w-full top-75vh z-10>
    <!-- 大标题 -->
    <section ml-15vw absolute>
      <div text-10 text-white font-bold tracking-widest v-html="data.titleList[Math.floor(Math.random() * data.titleList.length)]" />
      <div flex items-center>
        <div mr-4 flex gap-2>
          <div bg-red rounded-full h-3 w-3 />
          <div bg-yellow rounded-full h-3 w-3 />
          <div bg-green rounded-full h-3 w-3 />
        </div>
        <div text-4 text-white tracking-widest>
          Zako~ L菌
        </div>
      </div>
    </section>
    <!-- 个人简介 -->
    <section mx-9vw mt-90>
      <!-- 关于我 -->
      <div text-bold mb-4 ml-10 text-8 text-white>
        About Me
      </div>
      <div mx-10 mb-10 flex justify-between>
        <div class="text-white/80">
          <p leading-10>
            喵喵喵~ 你好，这里是L-Cat哟~
          </p>
          <p leading-10>
            热爱睡觉(嘿嘿)
          </p>
          <p leading-10>
            喜欢计算机科学和 IT 互联网事业，希望能成为一名优秀的开发者。
          </p>
          <p leading-10>
            正在用代码小魔法，让这个世界变得更加可爱和美好。通过巧妙地重用和扩展代码，构建出更美好的的数字世界。喵~
          </p>
          <p leading-10>
            Using a bit of code magic to make the world more adorable and wonderful. By cleverly reusing and extending code to create a more beautiful digital world. Meow~
          </p>
        </div>
        <div>
          <button class="transparent-button" @click.prevent="smoothScroll('AboutMe')">
          <img hidden rounded-full h-25 w-25 transition md:block hover:-translate-y-1 src="./assets/images/avatar.webp" alt="avatar">
          </button>
        </div>
      </div>

      <!-- 我的技能 -->
      <!-- <div text-bold mb-2 ml-10 text-8 text-white>
          My Skills
        </div> -->

      <!-- 我的项目 -->
      <div text-bold mb-2 ml-10 text-8 text-white>
        Projects
      </div>
      <div mb-10 flex flex-wrap justify-between>
        <div v-for="(item, index) in data.myProjects" :key="index" mx-10 my-4 class="basis-3/4 md:basis-1/6">
          <a :href="item.link">
            <div class="bg-white/5 hover:bg-white/10" p-2 rounded-lg shadow-md flex-col transition backdrop-blur-3xl backdrop-opacity-60 hover:backdrop-opacity-100 hover:-translate-y-2>
              <div text-bold opacity-75 text-white>
                {{ item.name }}
              </div>
              <div mt-1 opacity-50 text-3 text-white>
                {{ item.description }}
              </div>
            </div>
          </a>
        </div>
      </div>

      <!-- 社交链接 -->
      <div text-bold mb-2 ml-10 text-8 text-white id="AboutMe">
        Find Me
      </div>
      <div flex flex-wrap justify-between>
        <div v-for="(item, index) in data.socialLinks" :key="index" mx-10 my-4 class="basis-1/6">
          <a class="bg-white/5 hover:bg-white/10" p-2 rounded-lg shadow-md flex-col justify-between items-center transition backdrop-blur-3xl backdrop-opacity-60 hover:backdrop-opacity-100 hover:-translate-y-2 :href="item.link">
            <div mb-1 text-white f-c-c v-html="item.icon" />
            <div text-bold opacity-75 text-white>{{ item.label }}</div>
          </a>
        </div>
      </div>
    </section>

    <!-- 底部 -->
    <footer mb-5>
      <div class="text-white/60" mt-50 f-c-c>
        <i i-ant-design-environment-outlined mr-1 />
        <p>人生天地间，忽如远行客</p>
        <!--  <i i-ant-design-environment-outlined ml-1 /> -->
      </div>
      <div class="text-white/60" mt-2 f-c-c gap-4>
        <div>
          © 2019
          <span id="yearSpan" />
          L菌
        </div>
        <div text-pink-800>
          <a href="https://beian.miit.gov.cn">ICP: Undefined</a>
        </div>
      </div>
    </footer>
  </main>

  <!-- 背景 -->
  <div id="background" absolute wh-full left-0 top-0 z-0>
    <!-- 渐变阴影 -->
    <div to-black-500 absolute h-80vh w-full bottom--30vh left-0 from-black bg-gradient-to-t />
    <!-- 星轨背景 -->
    <StarTrails pb-45vh bg-black />
  </div>
</template>

<style lang="scss" scoped>
#background.fixed {
  position: fixed;
  top: -70%;
}

.transparent-button {
  background: transparent;
  border: none;
  color: inherit;
  text-decoration: none;
  cursor: pointer;
}
</style>
