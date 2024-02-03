<template>
  <div>
    <textarea v-model="keywords" placeholder="请输入关键词，每行一个"></textarea>
    <button @click="generateUrls">生成URLs</button>
    <ul>
      <li v-for="url in urls" :key="url">{{ url }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      keywords: '', // 存储用户输入的原始关键词
      urls: [], // 存储生成的URL列表
    };
  },
  methods: {
    generateUrls() {
      this.urls = this.keywords.split('\n') // 按行分割输入的关键词
        .filter(keyword => keyword.trim() !== '') // 过滤掉空行
        .map(keyword => `www.baidu.com/${encodeURIComponent(keyword)}`); // 将每个关键词转换成URL
    },
  },
};
</script>

<style scoped>
/* 在这里添加一些样式来美化你的组件 */
textarea {
  width: 100%;
  height: 100px;
}
button {
  margin: 10px 0;
}
</style>
