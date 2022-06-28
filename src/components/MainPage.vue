<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <li v-for="item in res_obj" :key="item.id">
      <PostContent :username="item.name" :content="item.content" />
    </li>
    <div class="form">
      <table>
        <tr>
          <th>Name</th>
          <td> <input type="text" v-model="name"></td>
        </tr>
        <tr>
          <th>Content</th>
          <td> <textarea rows="7" cols="60" class="field" v-model="content"></textarea></td>
        </tr>
        <tr>
          <td>
            <button v-on:click="SendPost" type="submit">Send</button>
          </td>
        </tr>
      </table>
      <p>{{ res_obj.name }}</p>
    </div>
  </div>

</template>

<script>
import PostContent from './PostContent.vue'
import axios from 'axios'

export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  created() {
    this.SendPost()
  },
  data: function () {
    return {
      name: "",
      content: "",
      idcount: 0,
      res_obj: {}
    }
  },
  methods: {
    SendPost() {
      axios.post("http://127.0.0.1:8080/api/post", {
        "id": this.count += 1,
        "name": this.name,
        "content": this.content
      })
        .then((response) => {
          console.log(response.data);
          var res = response.data;
          this.res_obj = res
          this.count = this.res_obj.length
        })
    }
  },
  components: {
    PostContent
  },

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
  display: list-item;
  list-style: none;
  margin: 0 10px;
}

a {
  color: #42b983;
}

input {
  float: left;
}

/* From uiverse.io */
button {
  padding: 1.3em 3em;
  font-size: 12px;
  text-transform: uppercase;
  letter-spacing: 2.5px;
  font-weight: 500;
  color: #000;
  background-color: rgb(139, 139, 139);
  border: none;
  border-radius: 45px;
  box-shadow: 0px 8px 1px rgba(0, 0, 0, 0.1);
  transition: all 0.3s ease 0s;
  cursor: pointer;
  outline: none;
}

button:hover {
  background-color: #c42323;
  box-shadow: 0px 15px 1px rgba(229, 46, 46, 0.4);
  color: #fff;
  transform: translateY(-3px);
}

button:active {
  transform: translateY(-1px);
}

.form {
  background-color: rgb(47, 47, 47);
  display: inline-block;
  border: none;
  border-radius: 10px;
}

textarea {
  resize: none;
  border: 1px solid #b3b3b3;
  border-radius: 10px;
  background-color: rgb(87, 87, 87) ;
  color:white;
}

input {
  border: 1px solid #b3b3b3;
  border-radius: 5px;
  background-color: rgb(87, 87, 87);
  color:white;
}

input,
select,
textarea,
button {
  font-size: 75%;
  font-family: 'Noto Sans JP', sans-serif;
}
</style>
