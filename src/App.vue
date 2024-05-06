<!-- แสดงผล -->
<template>
  <header>
    <h1>ระบบจัดการข้อมูลพนักงาน</h1>
  </header>
  <FormComponent @save="insertEmployee" />
  <!-- <div> -->
    <!-- <h1>Hello World</h1> -->
    <!-- <FormComponent/> -->
    <!-- <ListData :employees="employees" /> -->
    <section class="employee-content" v-if="employees.length>0">
      <h2>ข้อมูลพนักงานทุกคน</h2>
      <ListData :employees="employees"/>
    </section>
  <!-- </div> -->
</template>

<!-- การทำงาน -->
<script>
import FormComponent from './components/FormComponent.vue'
import ListData from './components/ListData.vue'
export default {
  name:"App",
  components:{
    ListData,
    FormComponent
  },
  // data(){
  //   return{
  //     // Dynamic Props
  //     employees:[
  //       {name:"Lufy",salary:30000},
  //       {name:"Solo",salary:25000},
  //       {name:"Sanji",salary:21000},
  //       {name:"Robin",salary:18000},
  //       {name:"Nami",salary:15000},
  //       {name:"Franky"},
  //       {name:"Usop",salary:11000},
  //       {name:"Chopper"}
  //     ]
  //   }
  // }
  data(){
    return{
      employees:[]
    }
  },
  methods:{
    insertEmployee(data){
      console.log("รับข้อมูลพนักงาน = " ,data);
      this.employees.push(data);
    }
  }
}
</script>

<!-- ตกแต่ง -->
<!-- Style Scoped -->
<!-- <style scoped>
  h1{
    background: orange;
  }
</style> -->

<style>
*{
  box-sizing: border-box;
}
body{
  margin: 0;
}
header{
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 3rem;
  border-radius: 10px;
  padding: 1rem;
  background-color: purple;
  color: #fff;
  text-align: center;
}
section.employee-content{
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 3rem;
  border-radius: 10px;
  padding: 1rem;
  text-align: center;
}
section.employee-content > h2{
  font-size: 2rem;
  border-bottom: 4px solid #ccc;
  color: purple;
  margin: 0 0 1rem 0;
}
</style>