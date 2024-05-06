<template>
  <!-- <div> -->
    <!-- <h1>{{ message }}</h1> -->
    <!-- Props (Parent to Children) -->
    <!-- <Person name="Ace" salary=30000 />
    <Person name="Lufy" salary=20000 />
    <Person name="Sabo" salary=15000 /> -->

    <!-- Dynamic Props -->
    <ul>
      <!-- <Card>พนักงานคนที่ 1</Card>
      <Card>พนักงานคนที่ 2</Card>
      <Card>พนักงานคนที่ 3</Card> -->
      <Person 
        v-for="item in employees" 
        :id="item.id" 
        :key="item.id" 
        :name="item.name" 
        :salary="item.salary" 
        :department="item.department" 
        :isVisible="item.isVisible"
        @show="toggleVisible"
        @delete="removeEmployee"
      />
      <!-- @show Custom Event (Children to Parent) -->
      <!-- @delete Custom Event (ลบข้อมูล) -->
    </ul>
  <!-- </div> -->
</template>

<script>
import Card from './Card.vue'
import Person from './Person.vue'
export default {
    name:"ListData",
    components:{
      Person,
      Card
    },
    data(){
        return{
            message:"แสดงรายชื่อพนักงานทุกคน"
        }
    },
    // props:["employees"]
    data(){
      return{
        // Dynamic Props
        employees:[
          {id:1,name:"Monkey D. Lufy",salary:30000,department:"กัปตัน",isVisible:false},
          {id:2,name:"Roronoa Solo",salary:25000,department:"นักดาบ",isVisible:false},
          {id:3,name:"Vinsmoke Sanji",salary:21000,department:"กุ๊ก",isVisible:false},
          {id:4,name:"Nico Robin",salary:18000,department:"นักประวัติศาสตร์",isVisible:false},
          {id:5,name:"Nami",salary:15000,department:"แมวขโมย",isVisible:false},
          {id:6,name:"Franky",salary:14000,department:"ช่างซ่อมเรือ",isVisible:false},
          {id:7,name:"Usop",salary:11000,department:"พลซุ่มยิง",isVisible:false},
          {id:8,name:"Tony Tony Chopper",salary:10000,department:"แพทย์",isVisible:false}
        ]
      }
    },
    // Custom Event (Children to Parent)
    methods:{
    toggleVisible(id){
      console.log("Child id = " + id);
      this.employees = this.employees.map((item)=>{
        if(item.id === id){
          return {...item,isVisible:!item.isVisible}
        }
        return item
      })
    },
    // Custom Event (ลบข้อมูล)
    removeEmployee(id){
      this.employees = this.employees.filter(item=>{
        return item.id !== id
      })
    }
  }
}
</script>

<!-- Style Scoped -->
<style scoped>
  /* h1{
    color: green;
  } */
  ul{
    list-style: none;
    margin: 1rem 0;
    padding: 0;
  }
</style>