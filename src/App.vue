<script setup>
import { ref } from 'vue'

const isMenuOpen = ref(false)
const navLinks = [
  { label: '菜单', href: '#menu' }, { label: '关于潮汐', href: '#story' },
  { label: '到店指南', href: '#visit' }, { label: '海味日记', href: '#journal' }
]
const dishes = [
  { image: 'https://images.unsplash.com/photo-1565680018434-b513d1e5d?auto=format&fit=crop&w=900&q=85', alt: '现烤海虾与时蔬', title: '鲜活海虾 · 现烤', description: '蒜香黄油 / 海盐 / 柠檬角', tag: '不限量' },
  { image: 'https://images.unsplash.com/photo-1534604973900-c43ab4c2e0ab?auto=format&fit=crop&w=900&q=85', alt: '丰盛海鲜拼盘', title: '海鲜大拼盘', description: '生蚝 / 扇贝 / 螃蟹 / 甜虾', tag: '不限量', featured: true },
  { image: 'https://images.unsplash.com/photo-1541544741938-0af808871cc0?auto=format&fit=crop&w=900&q=85', alt: '海鲜粥与热汤', title: '海鲜粥 · 暖暖一碗', description: '鲜虾 / 花蟹 / 瑶柱 / 葱花', tag: '现煮' }
]
const journalEntries = [
  { image: 'https://images.unsplash.com/photo-1601050690597-df0568f70950?auto=format&fit=crop&w=900&q=80', alt: '厨房里的新鲜海鲜食材', meta: '海鲜小知识 · 03.18.2024', title: '一只鲜虾，从海边到餐桌' },
  { image: 'https://images.unsplash.com/photo-1514933651103-005eec06c04b?auto=format&fit=crop&w=900&q=80', alt: '海鲜自助餐厅室内空间', meta: '关于潮汐 · 02.06.2024', title: '为什么我们希望你在这里吃到满足' }
]
const closeMenu = () => { isMenuOpen.value = false }
</script>

<template>
  <div class="announcement">今日鲜活海味已到港 · 晚市自助限时畅享 <span>→</span></div>
  <header class="nav-wrap"><nav class="nav container" :class="{ open: isMenuOpen }" aria-label="主导航">
    <a class="brand" href="#top" aria-label="TIDE 潮汐海鲜自助首页"><span class="brand-mark">潮</span><span><strong>TIDE</strong><small>潮汐海鲜自助</small></span></a>
    <button class="menu-toggle" aria-label="打开菜单" :aria-expanded="isMenuOpen" @click="isMenuOpen = !isMenuOpen"><span></span><span></span></button>
    <div class="nav-links"><a v-for="link in navLinks" :key="link.href" :href="link.href" @click="closeMenu">{{ link.label }}</a></div>
    <a class="nav-book" href="#booking">预约座位 <span>↗</span></a>
  </nav></header>

  <main id="top">
    <section class="hero container"><div class="hero-copy"><div class="eyebrow"><i></i> FRESH SEAFOOD BUFFET</div><h1>把大海，<br /><em>一口一口带上桌。</em></h1><p class="hero-desc">从鲜活海产到热气现烤，<br class="desktop" />想吃的海味，今天都可以尽情享用。</p><div class="hero-actions"><a class="button button-dark" href="#booking">预订自助席位 <span>↗</span></a><a class="text-link" href="#menu">看看今日海味 <span>↓</span></a></div></div><div class="hero-visual"><div class="hero-image"><img src="https://images.unsplash.com/photo-1559339352-11d035aa65de?auto=format&fit=crop&w=1200&q=85" alt="丰盛的新鲜海鲜自助餐台" /></div><div class="stamp"><span>EST.</span><strong>2021</strong><small>FRESH · DAILY</small></div><div class="leaf leaf-one">✦</div><div class="leaf leaf-two">✧</div></div></section>
    <section class="ticker" aria-label="餐厅理念"><div class="ticker-inner"><template v-for="item in 2" :key="item"><span>鲜 · 到港</span><b>✦</b><span>烤 · 现做</span><b>✦</b><span>聚 · 好吃</span><b>✦</b></template></div></section>
    <section class="intro container" id="story"><div class="section-kicker">01 / OUR SEAFOOD PHILOSOPHY</div><div class="intro-content"><h2>从海而来，<br /><span>把鲜味送到你桌边。</span></h2><div class="intro-text"><p>每天迎来一批批新鲜海产，虾、蟹、贝、鱼，喜欢什么就拿什么，现烤现煮，热腾腾地吃到满足。我们想做的，是一间让人放松下来的海鲜自助：和家人朋友围坐一桌，放开吃，也开心聊。</p><a class="circle-link" href="#menu">了解<br />更多 <span>↗</span></a></div></div></section>
    <section class="menu-section" id="menu"><div class="container menu-head"><div><div class="section-kicker">02 / ALL YOU CAN EAT</div><h2>今日海味，<em>新鲜不限量。</em></h2></div><a class="text-link dark-link" href="#booking">查看自助时段 <span>↗</span></a></div><div class="dishes container"><article v-for="(dish, index) in dishes" :key="dish.title" class="dish-card" :class="{ featured: dish.featured }"><div class="dish-img"><img :src="dish.image" :alt="dish.alt" /><span>0{{ index + 1 }}</span></div><div class="dish-meta"><div><h3>{{ dish.title }}</h3><p>{{ dish.description }}</p></div><strong>{{ dish.tag }}</strong></div></article></div></section>
    <section class="booking container" id="booking"><div class="booking-card"><div><div class="section-kicker light">03 / YOUR SEAFOOD TABLE AWAITS</div><h2>今晚，<br /><em>放开吃海鲜。</em></h2></div><div class="booking-right"><p>午市 11:30 — 14:00 · 晚市 17:30 — 22:30<br />儿童友好 · 建议提前预约</p><a class="button button-light" href="mailto:hello@tide-seafood.cn">预约自助席位 <span>↗</span></a></div></div></section>
    <section class="visit container" id="visit"><div class="visit-copy"><div class="section-kicker">04 / FIND US</div><h2>来潮汐，<br /><em>一起吃顿尽兴的。</em></h2><p>上海市徐汇区武康路 218 号<br />每日营业 · 午晚市均提供海鲜自助</p><a class="text-link" href="https://maps.google.com" target="_blank" rel="noreferrer">打开地图 <span>↗</span></a></div><div class="map-art" aria-label="餐厅位置示意图"><div class="map-road road-a"></div><div class="map-road road-b"></div><div class="map-road road-c"></div><div class="map-pin">潮</div><span class="map-label label-a">WUKANG RD.</span><span class="map-label label-b">HUAIHAI RD.</span></div></section>
    <section class="journal container" id="journal"><div class="journal-head"><div><div class="section-kicker">05 / FROM THE SEAFOOD JOURNAL</div><h2>关于海鲜，<br />也关于一起吃饭。</h2></div><a class="text-link dark-link" href="#journal">浏览海味日记 <span>↗</span></a></div><div class="journal-grid"><article v-for="entry in journalEntries" :key="entry.title"><div class="journal-image"><img :src="entry.image" :alt="entry.alt" /></div><span>{{ entry.meta }}</span><h3>{{ entry.title }}</h3></article></div></section>
  </main>
  <footer><div class="container footer-main"><a class="brand footer-brand" href="#top"><span class="brand-mark">潮</span><span><strong>TIDE</strong><small>潮汐海鲜自助</small></span></a><div class="footer-links"><a v-for="link in navLinks.slice(0, 3)" :key="link.href" :href="link.href">{{ link.label }}</a><a href="mailto:hello@tide-seafood.cn">联系我们</a></div><div class="socials"><a href="#">IG</a><a href="#">小红书</a></div></div><div class="container footer-bottom"><span>© 2024 TIDE SEAFOOD BUFFET. ALL RIGHTS RESERVED.</span><span>沪 ICP 备 20240118 号</span></div></footer>
</template>
