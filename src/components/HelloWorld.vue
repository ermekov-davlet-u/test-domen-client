<template>
  <div class="hello">
    <h2>
      {{
        text
      }}
    </h2>
  <PostElem :newValue="123 + 23234" @interface="hundleClick"/>
  </div>
</template>

<script>
import PostElem from "./PostForm.vue"
export default {
  name: 'HelloWorld',
  components: {PostElem},
  data: () => {
    return{
      text: "",
    }
  },
  props: {
    msg: String
  },
  methods: {
    async hundleClick(param) {
      const existDomen = await fetch("http://127.0.0.1:8000/api/domen?test=" + param).then(res => res.json())
      if(existDomen.available){
        this.text = "Домен " + existDomen.data + " свободен."
      }else{
        this.text = "Домен " + existDomen.data + " занят."
      }
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
