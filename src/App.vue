<template>
  <div>
    <Header></Header>
    <div :style="{ width: '70%', margin: 'auto' }">
      <el-container>
        <el-aside :style="{ width: '25%' }">
          <div :style="{ display: 'flex', flexWrap: 'wrap', width: '100%' }">
            <Tag
              v-for="(tag, index) in tags"
              :key="index"
              :data="tag"
              @choose="handleChooseTag"
            ></Tag>
          </div>
        </el-aside>
        <el-container :style="{ width: '70%' }">
          <router-view />
        </el-container>
      </el-container>
    </div>
  </div>
</template>

<script>
import Header from './components/layout/Header.vue';
import Tag from './components/UIComponent/Tag.vue';
import tags from './mockup/tag.json';
export default {
  name: 'App',
  components: { Header, Tag },
  data() {
    return {
      tags,
    };
  },
  methods: {
    handleChooseTag(e) {
      this.$store.commit('CHANGE_TAG', e);
      this.$router.push(`/tags/${e}`);
    },
  },
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Commissioner&display=swap');

html,
body {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  padding: 0;
  margin: 0;
}
</style>
