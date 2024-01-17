<template>
  <q-page class="flex flex-center ">
    <q-card class="my-card">
      <q-card-section >
        <div class="text-h4"> To-Do-List</div>
      </q-card-section>
      <q-card-section >
       <div class="row justify-center">
        <div class="col-12">
           <q-input v-model=" toDoTask" label="Input Task" >
            <template v-slot:after>
              <q-btn round dense flat icon="send" @click=" addItem"/>
            </template>
            </q-input>

        </div>
       </div>
      </q-card-section>
      <q-separator/>
      <q-card-section v-if="toDolist.length >0 " >
        <div class="row justify-center" v-for="(item , index) in  toDolist" :key="index">
          <div class="col-8">
            {{item.value}}
             </div>
             <div class="col-auto py-md">
              <q-btn round dense flat icon="done" @click=" removeItem(index)"/>

             </div>


        </div>
        </q-card-section>
        <q-card-section v-else >
       <div class="row justify-center">
        <div class="col-12">
          <div class="text-h6">
            No Item In The List
        </div>

        </div>
        </div>
        </q-card-section>
    </q-card>
  </q-page>
</template>

<script>
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'IndexPage',
  data(){
    return {
      toDoTask:'',
      toDolist:[
        {value : "create an app"},
        {value : "Build an app"}
      ]
    }
  },
  methods:{
    addItem(){
      this.toDolist.push({value : this.toDoTask})
    },
    removeItem(index){
      this.toDolist.splice(index, 1)

    },
  }
})
</script>
