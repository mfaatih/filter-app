<template>
  <div>
    <md-card :key="post.phone" v-for="post in filteredList">
      <md-card-header>
        <md-card-header-text>
          <div class="md-title">
            {{ post.name.title }} {{ post.name.first }} {{ post.name.last }}
          </div>
          <div class="md-subhead">{{ post.location.city }}</div>
        </md-card-header-text>

        <md-card-media md-medium>
          <img :src="post.picture.medium" alt="People" class="photo" />
        </md-card-media>
      </md-card-header>
    </md-card>
  </div>
</template>

<script>
export default {
  props: ['posts', 'type'],
  data() {
    return {};
  },
  computed: {
    filteredList() {
      return this.posts.filter(post => {
        return post.name.first.toLowerCase().includes(this.type.toLowerCase());
      });
    },
  },
};
</script>

<style>
.md-card {
  width: 320px;
  margin: 10px;
  display: inline-block;
  vertical-align: top;
  transition: transform 1s !important;
}
.md-card:hover {
  transform: scale(1.1);
}
.photo {
  width: 150px !important;
}
</style>
