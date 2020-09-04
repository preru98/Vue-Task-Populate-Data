<template>
  <div class="populate">
    <h1>Populate</h1>
    <table v-if="repoData.length" id="query-table" border="1 px">
        <tr>
            <td>Email</td>
            <td>Query</td>
        </tr>
        <tr v-for="record in repoData" :key="record.email">
            <td>{{ record.email }}</td>
            <td>{{ record.query }}</td>
        </tr>
    </table>
    <p v-else>Not available</p>

  </div>
</template>

<script>
import * as axios from 'axios'
export default {
  name: 'PopulateData',
  data: function(){
    return {
        repoData :[
            {
                "email": "admin@argames1.com",
                "query": "testing1"
            },
            {
                "email": "admin@argames2.com",
                "query": "testing2",
            }
        ]
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
