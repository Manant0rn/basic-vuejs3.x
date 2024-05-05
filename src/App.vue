<!-- แสดงผล -->
<template>
  <div>
    <h1>Hello World</h1>
    <FormComponent/>
    <ListData/>
  </div>
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
  }
}
</script>

<!-- ตกแต่ง -->
<style>

</style>