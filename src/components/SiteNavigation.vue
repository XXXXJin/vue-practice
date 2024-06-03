<template>
  <header class="bg-gray-100 sticky top-0">
    <nav class="container flex justify-between items-center h-16">
      <RouterLink :to="{name: 'home'}">
        <div class="flex gap-3 items-center text-2xl">
          <i class="fa-solid fa-cloud text-blue-300"></i>
          <p class="">天気予報</p>
        </div>
      </RouterLink>
      <div class="flex items-center gap-3">
        <i class="fa-solid fa-circle-info cursor-pointer hover:text-gray-600" title="使い方の説明" v-on:click="toggleModel"></i>
        <i class="fa-solid fa-plus cursor-pointer hover:text-gray-600" title="場所を追加する"></i>
      </div>
      <BaseModal v-bind:isModelActice="isModelActice" v-on:close-modal="toggleModel">
        <h2 class="mb-2 text-xl font-bold tracking-tight text-gray-900">このサイトについて</h2>
        <p class="font-normal text-gray-700">このアプリはvueの基本の使い方を学ぶために作成したもので、指定した場所の天気情報を取得することができます。</p>
        <h2 class="mb-2 text-xl font-bold tracking-tight text-gray-900 mt-6">使い方</h2>
        <p class="font-normal text-gray-700">ヘッダーのプラスボタンを押して、地名を選択してください。</p>
      </BaseModal>
    </nav>
  </header>
</template>

<script setup>
import BaseModal from './BaseModal.vue';
import {ref} from 'vue';

const isModelActice = ref(null);

const toggleModel = () => {
  isModelActice.value = !isModelActice.value;
}

</script>
