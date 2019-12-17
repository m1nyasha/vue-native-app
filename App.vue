<template>
  <scroll-view class="container" :style="{
    paddingTop: 15,
    paddingLeft: 10,
    paddingRight: 10,
  }">
    <view
          class="post"
          :style="{
            marginTop: 10,
            padding: 10,
            borderWidth: 2,
            borderRadius: 10,
            borderColor: '#e3e3e3'
          }"
          v-for="post in posts"
    >
      <text class="title">{{post.title}}</text>
      <text class="text">{{post.body}}</text>
      <view>
        <button
              title="Подробнее"
              :styles="{
                color: '#fff',
                backgroundColor: '#5471af'
              }"
        />
      </view>
    </view>
  </scroll-view>
</template>

<script>
  export default {
    data() {
      return {
        posts: []
      }
    },
    async mounted () {
      this.getPosts();
    },
    methods: {
      async getPosts() {
        let res = await fetch(`https://jsonplaceholder.typicode.com/posts?_limit=10`);
        this.posts = await res.json();
      }
    }
  }
</script>

<style>
  .container {
    background-color: white;
    width: 100%;
  }
  .title {
    color: #5471af;
    font-size: 20px;
    font-weight: bold;
  }
</style>
