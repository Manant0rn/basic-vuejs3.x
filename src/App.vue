<template>
  <section>
    <!--  Interpolation และ v-html -->
    <!-- การอ้างอิง properties
    ใน template ใช้ {{  }}
    ใน script keyword:this -->
    <!-- <h1>ชื่อผู้สมัคร : {{ firstname }}</h1>
    <h1>นามสกุล : {{ lastname }}</h1>
    <h1>อายุ : {{ age }} ปี</h1> -->
    <!-- v-html คือมอง tag ใน data ที่เป็น html มาแสดงผล -->
    <!-- <p>ที่อยู่ : <span v-html="address"></span></p> -->

    <!-- การอ้างอิง methods
    ใน template ใช้ {{ ชื่อ methods }}
    ใน script keyword:this.ชื่อ method -->
    <!-- <h1>ชื่อ - นามสกุล : {{ getFullName() }}</h1>
    <h1>อายุ : {{ age }} ปี</h1>
    <p>ที่อยู่ : <span v-html="address"></span></p> -->

    <!-- การใช้ Attribute Binding เป็นการ bunding กับตัว data กับ attribute ใช้ได้ 2 แบบ v-bind หรือ : -->
    <!-- <img v-bind:src="picture" alt="" v-bind:width="size" v-bind:height="size"> -->
    <img :src="picture" alt="" :width="size" :height="size">
    <h1>ชื่อ - นามสกุล : {{ getFullName() }}</h1>
    <h1>อายุ : {{ age }} ปี</h1>
    <p>ที่อยู่ : <span v-html="address"></span></p>
    <p><a :href="social" target="_newblank">Youtube</a></p>
    <!-- Data Array -->
    <p>งานอดิเรก</p>
    <ul>
      <li>{{ hobby[0] }}</li>
      <li>{{ hobby[1] }}</li>
      <li>{{ hobby[2] }}</li>
    </ul>
    <!-- Data Object -->
    <p>ข้อมูลพื้นฐาน : </p>
    <ul>
      <li>เพศ : {{ general.gender }}</li>
      <li>น่้ำหนัก : {{ general.weight }} kg</li>
      <li>ส่วนสูง : {{ general.height }} cm</li>
      <li>โรคประจำตัว : {{ general.status }}</li>
    </ul>
  </section>
</template>

<script>

export default {
  name: 'App',
  // Interpolation และ v-html
  // การอ้างอิง properties
  // ใน template ใช้ {{  }}
  // ใน script keyword:this
  data(){
    return{
      firstname:"Manantorn",
      lastname:"Sapsamnieng",
      age:27,
      address:"<strong>กรุงเทพมหานคร</strong>",
      picture:"https://t3.ftcdn.net/jpg/05/53/79/60/360_F_553796090_XHrE6R9jwmBJUMo9HKl41hyHJ5gqt9oz.jpg",
      size:150,
      social:"https://www.youtube.com",
      // Data Array 
      hobby:["เล่นกีฬา","เล่นเกมส์","ดูหนัง"],
      // Data Object
      general:{gender:"ชาย",weight:82.4,height:170,status:false}
    }
  },
  // การอ้างอิง methods
  // ใน template ใช้ {{ ชื่อ methods }}
  // ใน script keyword:this.ชื่อ method
  methods:{
    getFullName(){
      // ถ้าในพื้นที่เดียวกัน ใช้ this แต่คิดว่าถ้าเป็นการส่งข้อมูลจากอีกหน้าหนึ่งมา ไม่ต้องใช้
      // return this.firstname + this.lastname
      return `${this.firstname}  ${this.lastname}`
    }
  }
}
</script>

<style>

</style>