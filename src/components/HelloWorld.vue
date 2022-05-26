<template>
  <div class="hello">
    <button type="button" @click="playLocalAudio">本地音频</button>
    <button type="button" @click="playDatabaseAudio">数据库音频</button>
  </div>
</template>

<script>
import axios from 'axios';
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  methods: {
    //本地音频，从public/static中取音频
    playLocalAudio() {
      const loacalUrl = `${location.protocol}//${location.host}/static/test1.mp3`
      new Audio(loacalUrl).play();
    },
    //数据库音频，从数据库中取音频文件（这里是通过mock）
    playDatabaseAudio() {
      axios.get('/api/tests').then(response => {
        new Audio(response.data.value).play();
      });
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
