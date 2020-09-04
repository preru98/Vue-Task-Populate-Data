<template>
  <div class="populate">
    <h1>Populate</h1>
    <table v-if="repoData.length" id="query-table">
        <tr>
            <th>Email</th>
            <th>Query</th>
            <th>Query Date</th>
        </tr>
        <tr v-for="record in repoData" :key="record.query"> <!-- Ideally it should be email -->
            <td>{{ record.email }}</td>
            <td>{{ record.query }}</td>
            <td>{{ record.createdAt }}</td>
            
        </tr>
    </table>
    <p v-else>Not available</p>
  </div>
</template>

<script>
import * as axios from 'axios'
export default {
    name : 'PopulateData',
    data : () => {
        return {
            repoData:[]
        }
    },
    mounted : function(){
        axios({
            method: 'post',
            url: 'http://66.175.217.67:3020/argames/getQuery',
            data: {
                "checkFilter":""
            },
            headers: {
                Authorization: `Bearer 5afe34f322478bc5352a3d988ed4ccb18f7a409160339038c83c772c8a6a7387eb3caf90d064861965eec7eb210286ba` 
            }
        })
        .then( (response) => {   
            console.log(response.data);
            console.log(this);
            this.repoData = response.data.result;
            console.log(this.repoData);
        })
        .catch( (error) => {
            console.log(error);
        })
    }
    
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
/* h3 {
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
} */
table {
    width :100%;
    border-collapse: collapse;
}
th{
    color:black;
    font-weight: 700;
    text-align: center;
    border : 1px solid grey;
    padding : 10px;
}
table, td {
    border : 1px solid grey;
    text-align : left;
    padding : 10px;
}
body{
    color:black;
}
tr:nth-child(odd) {
    background-color: #F2F2F8;
}


</style>
