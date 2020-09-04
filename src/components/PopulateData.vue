<template>
  <div class="populate">
    <h1>Populate</h1>
    <table v-if="repoData.length" id="query-table">
        <tr>
            <th>Email</th>
            <th>Query</th>
            <th>Query Date</th>
            <th>Action</th>
        </tr>
        <tr v-for="record in repoData" :key="record.query"> <!-- Ideally it should be email -->
            <td>{{ record.email }}</td>
            <td>{{ record.query }}</td>
            <td>{{ record.createdAt }}</td>
            <td style= "text-align:center;"><img src="../assets/action.png" alt="action"></td>
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
            this.repoData = response.data.result;
        })
        .catch( (error) => {
            console.log(error);
        })
    }
    
}
</script>

<style scoped>
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
