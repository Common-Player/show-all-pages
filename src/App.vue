<template>
  <div class="url-generator">
    <textarea v-model="keywords" rows="5"></textarea>
    <div class="input-group">
      <label for="prefix">自定义前缀</label>
      <input id="prefix" v-model="prefix" />
      <label for="suffix">自定义后缀</label>
      <input id="suffix" v-model="suffix" />
      <button @click="generateUrls">生成URL</button>
    </div>
    <textarea v-model="generatedUrls" rows="10" readonly></textarea>
  </div>
</template>

<script>
export default {
  data() {
    return {
      keywords: '',
      generatedUrls: '',
      prefix: 'https://m.baidu.com/s?word=', // 新增自定义前缀
      suffix: '', // 新增自定义后缀
    };
  },
  methods: {
    generateUrls() {
      const urls = this.keywords.split('\n').map(keyword => 
        this.prefix + encodeURIComponent(keyword) + this.suffix
      ).join('\n');
      this.generatedUrls = urls;
    },
  },
};
</script>

<style>
.url-generator {
  display: flex;
  flex-direction: column;
  gap: 10px;
  margin: 20px;
}

.input-group {
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  gap: 10px;
}

.url-generator textarea, .url-generator button, .url-generator input {
  padding: 10px;
  font-size: 16px;
  border-radius: 5px;
  border: 1px solid #ccc;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
  transition: box-shadow 0.3s ease, border-color 0.3s ease;
}

.url-generator label {
  white-space: nowrap;
}

.url-generator button {
  padding: 10px 20px;
  cursor: pointer;
  background-color: #4CAF50;
  color: white;
  border: none;
}

.url-generator button:hover {
  background-color: #45a049;
  box-shadow: 0 4px 8px rgba(0,0,0,0.2);
}

.url-generator textarea:focus, .url-generator button:focus, .url-generator input:focus {
  border-color: #4CAF50;
  box-shadow: 0 0 0 2px rgba(76,175,80,0.5);
}
</style>
