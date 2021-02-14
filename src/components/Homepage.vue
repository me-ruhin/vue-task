<template>
        <div>
          
            <table>
                 <tr>
                     <td colspan="2">  <input v-model="task"  @keyup.enter="adddData()" /> </td>
                </tr>                

                <tr>
                    <th>Company</th>
                 
                </tr>
                <tr v-for="(list,index) in taskList" :key="index"><td><input type="checkbox" @click="changeStatus(index)"  /> <input type="text" :class="hideborder" @keyup.enter="updateTask(index)"  v-model="list.name"></td>
                    
                </tr>
               
            </table>
            <button @click="allTaskLists()">All </button>
            <button @click="activeTask()">Active </button>
            <button @click="completedTask()">Completed </button>
            
        </div>

</template>

<script>
export default {

    data(){
        return{
            taskList:[
                {name:'rahim',status:1},
                {name:'abcd',status:0},
                {name:'kuddosh',status:1},
                {name:'Rahman',status:1},
                {name:'abul',status:1},
                ],
            tempTaskList:[],
            task:'',
            hideborder:'hideborder',
            updateValue:'',
        }
    },
    methods:{
          adddData(){
             this.taskList.push(this.task)
             this.task="";
         },
         updateTask(index){


             console.log(this.taskList[index].name)
         },
         completedTask(){
                this.taskList=[];
         },
         changeStatus(index){
              console.log(index);
         },
         activeTask(){

         this.taskList =   this.taskList.filter(item=>{
                if(item.status == 1){
                    return true
                }
            });
             return this.taskList;
         },


        allTaskLists(){
         
             return this.taskList;
         }



         

    }
    
}
</script>

<style scoped>

table {
  font-family: arial, sans-serif;
  border-collapse: collapse;
  width: 100%;
  /* margin: 0 auto; */
}

 

 

.hideborder{
    border: 0;
}
</style>