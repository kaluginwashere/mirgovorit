<template>
  <div class="container">
    <author-info v-if="info.author"
                 :topic="info.author.topic"
                 :name="info.author.name"
                 :description="info.author.description"
                 :avatar="info.author.avatar"
    ></author-info>
    <div>
      <curse-card v-for="seminar in info.seminars"
                  :key="seminar"
                  :title="seminar.title"
                  :type="seminar.type"
                  :description="seminar.description"
                  :curators="seminar.curators"
                  :methodists="seminar.methodists"
                  :link="seminar.link"
                  :price="seminar.price"
                  :date-start="seminar.dateStart"
                  :duration="seminar.duration"
      ></curse-card>
    </div>
  </div>
</template>

<script>
import AuthorInfo from "@/components/AuthorInfo";
import CurseCard from "@/components/CurseCard";
import axios from 'axios'


export default {
  name: 'App',
  components: {
    AuthorInfo,
    CurseCard,
  },
  data() {
    return {
      info: [],
      author: [],
      seminars: []
    }
  },
  mounted() {
    axios
        .get('https://eg-cdn.s3.eu-central-1.amazonaws.com/static/fe-test/seminars-test-data.json')
        .then(response => (
            this.info = response.data
            // console.log(response.data)
        ))
        .catch(error => (
            console.log(error)
        ));
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
