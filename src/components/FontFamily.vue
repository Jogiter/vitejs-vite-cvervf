<template>
  <div class="p-4 sticky top-0 left-0 right-0 bg-white shadow-xl">
    <h2 class="text-xl">font-family</h2>
    <div>
      <label class="w-[200px] inline-block" for="size"
        >select font-size:{{ ssize }}</label
      >
      <input
        type="range"
        v-model="ssize"
        :min="smin"
        :max="smax"
        :step="sstep"
      />
    </div>
    <div>
      <label class="w-[200px] inline-block" for="size"
        >select font-weight:{{ sweight }}</label
      >
      <input
        type="range"
        v-model="sweight"
        :min="wmin"
        :max="wmax"
        :step="wstep"
      />
    </div>
  </div>
  <hr class="my-5" />

  <section class="p-4 grid gap-x-8 gap-y-4 grid-cols-1 lg:grid-cols-5">
    <div
      :class="font"
      :style="{
        'font-size': ssize + 'px',
        'font-weight': sweight,
      }"
      v-for="font of classFonts"
      :key="font"
    >
      <h4>{{ font }}</h4>
      <Content />
    </div>

    <div
      :style="{
        'font-family': font,
        'font-size': ssize + 'px',
        'font-weight': sweight,
      }"
      v-for="font of [...styleFonts, ...SCFonts]"
      :key="font"
    >
      <h4>{{ font }}</h4>
      <Content />
    </div>
  </section>

  <hr />
  <h2 class="mx-4">繁体字</h2>
  <section class="p-4 grid gap-x-8 gap-y-4 grid-cols-1 lg:grid-cols-2">
    <div
      :style="{
        'font-family': font,
        'font-size': ssize + 'px',
        'font-weight': sweight,
      }"
      v-for="font of TCFonts"
      :key="font"
    >
      <h4>{{ font }}</h4>
      <p>{{ tc }}</p>
    </div>
  </section>
</template>

<script setup lang="tsx">
import { ref } from 'vue'
import Content from './Content.vue'

const classFonts = [
  'font-sans',
  'font-serif',
  'font-mono'
]

const styleFonts = [
  'San Francisco',
  'Roboto',
]

const SCFonts = [
  'Hiragino Sans GB',
  'Microsoft Yahei',
  'Simhei',
  'Hiragino',
  'SimSun',
]

const TCFonts = [
  'Microsoft JhengHei',
  'MingLiU',
  'MingLiU_HKSCS',
  'I.Ming'
]

const tc  = '提供加密貨幣支付服務連接商家與客戶，建立支付、收款通道。企業化管理服務提供商家日常的資產、運營、客戶、員工等多維度管理'

const sizes = [
  'text-sm',
  'text-md',
  'text-lg',
  'text-xl',
  'text-2xl'
]

const weights = [
  400,
  500,
  600,
  700
]
const ssize = ref(20)
const [smin, smax, sstep] = [12, 100, 2]

const sweight = ref(400)
const [wmin, wmax, wstep] = [100, 900, 100]
</script>
