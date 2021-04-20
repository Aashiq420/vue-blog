<template>
<div class="home">
  <h1>Home</h1>
  <div v-if="error">{{ error }}</div>
  <div v-if="posts.length">
  <PostList :posts="posts" />
  </div>
  <div v-else>Loading... </div>
  <!-- <button @click="showPosts = !showPosts">Toggle posts</button>
  <button @click="posts.pop()">Delete a post</button> -->
</div>
  <!-- <input type="text" v-model="search">
  <p>Search term - {{ search }}</p>
  <div v-for="name in matchingNames" :key="name">
    {{ name }}
  </div>
  <button @click="handleClick">Stop watching</button> -->
</template>

<script>
//import: ref, computed, watch, watchEffect
import PostList from '../components/PostList.vue'
import getPosts from '../composables/getPosts'


export default {
  name: 'Home',
  components: { PostList },
  setup() {
    const { posts, error, load } = getPosts()

    load()

    //const showPosts = ref(true)
    return { posts, error }//, showPosts }
  }
  //   const search = ref('')
  //   const names = ref(['luffy','zoro','nami','usopp','sanji','chopper','robin','franky','brook'])

  //   const stopWatch = watch(search, () => {
  //     console.log('watch function ran')
  //   })

  //   const stopEffect = watchEffect(() => {
  //     console.log('watchEffect function ran', search.value)
  //   })

  //   const matchingNames = computed(() => {
  //     return names.value.filter((name) => name.includes(search.value))
  //   })

  //   const handleClick = () => {
  //     stopWatch()
  //     stopEffect()
  //   }

  //   return { names, search, matchingNames, handleClick }
  // }

}
</script>
