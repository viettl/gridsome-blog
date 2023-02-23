<template>
  <Layout>
    <header class="header">
      <h1 v-html="$page.metadata.siteName" />
      <h2 v-html="$page.metadata.siteDescription" />
    </header>
    <section class="posts">
      <PostList v-for="post in $page.allPost.edges" :key="post.node.id" :post="post.node" />
    </section>
  </Layout>
</template>
<script>

import PostList from '../components/PostList.vue';
export default {
  metaInfo: {
    title: 'Hello, world!',
  },
  components: {
    PostList,
  },
};
</script>

<style>
.header {
  font-family: "Stylish";
  font-size: 35px;
  text-align: center;
  line-height: 1.4em;
  padding: 0.7em;
}
.header h2 {
  font-weight: 200;
  font-size: 35px;
}
</style>

<!-- gridsome has a centralized data management for all your data, which in our case is GraphQL -->

<page-query>
query {
  metadata {
    siteName
    siteDescription
  }
 allPost {
  totalCount
  edges {
    node {
      id
      title
      timeToRead
      description
      date(format: "MMMM DD, YYYY")
      path
    }
  }
 }
}
</page-query>
