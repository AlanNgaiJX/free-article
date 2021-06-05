<template>
  <div id="app">
    <ul class="subject-list">
      <li
        class="subject-item"
        v-for="(subject, subjectName) in subjectsMap"
        :key="subjectName"
      >
        {{ subjectName }}
        <ul class="article-list">
          <li
            class="article-item"
            v-for="article in subject"
            :key="article.href"
            @click="toArticle(article.fileName)"
            v-show="!article.needPay"
          >
            {{ article.title }}
          </li>
        </ul>
      </li>
    </ul>
  </div>
</template>

<script>
import subjectsMap from "@/config/subjectsMap.json";
export default {
  name: "App",
  data() {
    return {
      subjectsMap,
      host: 'https://alanngai1996.xyz/store/w3c-plus-free/htmls/'
    };
  },
  methods:{
    toArticle(fileName){
      window.open(this.host + fileName);
    }
  }
};
</script>

<style lang="scss">
.subject-list {
  font-size: 18px;

  .subject-item {
    border: 1px solid #eee;
    margin-bottom: 100px;
    padding: 20px;
  }
  .article-list {
    padding-left: 20px;
    padding-top: 20px;
    display: grid;
    grid-template-columns: repeat(3, 1fr) ;

    .article-item {
      font-size: 16px;
      margin-bottom: 15px;
      line-height: 30px;
      cursor: pointer;

      &:hover{
        color: red;
      }
    }
  }
}
</style>
