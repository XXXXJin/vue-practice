<template>
  <header class="bg-gray-100 sticky top-0">
    <nav class="container flex justify-between items-center h-16">
      <RouterLink :to="{ name: 'home' }">
        <div class="flex gap-3 items-center text-2xl">
          <i class="fa-solid fa-cloud text-blue-300"></i>
          <p class="">天気予報</p>
        </div>
      </RouterLink>
      <div class="flex items-center gap-3">
        <i
          class="fa-solid fa-circle-info cursor-pointer hover:text-gray-600"
          title="使い方の説明"
          v-on:click="toggleModel"
        ></i>
      </div>
      <BaseModal v-bind:isModelActice="isModelActice" v-on:close-modal="toggleModel">
        <h2 class="mb-2 text-xl font-bold tracking-tight text-gray-900">このサイトについて</h2>
        <p class="font-normal text-gray-700">
          このアプリはvueの基本の使い方を学ぶために作成したものであり、指定した場所の天気情報を取得することができます。
        </p>
        <h2 class="mb-2 text-xl font-bold tracking-tight text-gray-900 mt-6">使い方</h2>
        <p class="font-normal text-gray-700">
          検索ボックスで都市名を英語で検索してください。検索結果をクリックして、詳細ページへと遷移できます。詳細ページで都市をお気に入りに追加と削除が可能です。お気に入りに追加された都市はトップページにリストアップされます。
        </p>
      </BaseModal>
    </nav>
  </header>
</template>

<script setup>
import BaseModal from './BaseModal.vue'
import { ref } from 'vue'

const isModelActice = ref(null)

const toggleModel = () => {
  isModelActice.value = !isModelActice.value
}
</script>
