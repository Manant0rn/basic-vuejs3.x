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
    <img :src="picture" alt="" :width="size" :height="size" ref="imageEl"/><br>

    <!-- event modifier -->
    <!-- <form @submit.prevent="submitForm">
      <label>ป้อนชื่อเล่น:</label> -->
      <!-- Ref DOM Element -->
      <!-- <input type="text" v-on:input="setNickname" ref="nicknameEl"> -->
      <!-- <input type="text" ref="nicknameEl">
      <button type="submit">บันทึก</button>
    </form> -->

    <!-- eventinput -->
    <!-- ป้อนชื่อเล่น : <input type="text" v-on:input="setNickname"/> -->
    <!-- <h1>ชื่อ - นามสกุล : {{ getFullName() }}</h1> -->
    <h1>ชื่อ - นามสกุล : {{ getFullName }}</h1>
    <!-- <h2>ชื่อเล่น {{ nickname }}</h2> -->
    <h1>อายุ : {{ age }} ปี</h1>
    <h1>เงินเดือน : {{ salary }} บาท</h1>
    <!-- <h1>รายได้ต่อปี : {{ getincome }} บาท</h1> -->
    <h1>ตำแหน่งงาน : {{ getDepartment }}</h1>
    <button @click="addSalary(5000)">เพิ่มเงินเดือน</button>
    <h2>Method1 : {{ getRandomByMethod() }}</h2>
    <h2>Method2 : {{ getRandomByMethod() }}</h2>
    <hr/>
    <h2>Computed1 : {{ getRandomByComputed }}</h2>
    <h2>Computed2 : {{ getRandomByComputed }}</h2>
    
    <!-- ซ่อน/แสดง Element (v-show) -->
    <button @click="toggleVisible">{{ isVisible ? "ซ่อน" : "แสดง"}}รายละเอียด</button>
    <article v-show="isVisible">
      <p>ที่อยู่ : <span v-html="address"></span></p>
      <p><a :href="social" target="_newblank">Youtube</a></p>
      <!-- Data Array -->
      <!-- <p>งานอดิเรก</p>
      <ul>
        <li>{{ hobby[0] }}</li>
        <li>{{ hobby[1] }}</li>
        <li>{{ hobby[2] }}</li>
      </ul> -->
      <!-- Render Condition (v-if/v-else) -->
      <p v-if="hobby.length === 0">ไม่มีงานอดิเรก</p>
      <div v-else>
        <p>งานอดิเรก :</p>
        <ul>
          <!-- <li>{{ hobby[0] }}</li>
          <li>{{ hobby[1] }}</li>
          <li>{{ hobby[2] }}</li> -->
          <!-- List Data ด้วย v-for (Array) -->
          <li v-for="(item,index) in hobby" :key="index">{{ item }}</li>
        </ul>
      </div>
      <!-- Data Object -->
      <p>ข้อมูลพื้นฐาน : </p>
      <ul>
        <!-- <li>เพศ : {{ general.gender }}</li>
        <li>น่้ำหนัก : {{ general.weight }} kg</li>
        <li>ส่วนสูง : {{ general.height }} cm</li>
        <li>โรคประจำตัว : {{ general.status }}</li> -->
        <!-- List Data ด้วย v-for (Object) -->
        <li v-for="(item,key) in general" :key="key">{{ key }} - {{ item }}</li>
      </ul>
      <!-- Event -->
      <!-- <button v-on:click="showData">คลิกเพื่อดูข้อมูล</button> -->
      <!-- ลดรูป -->
      <!-- <button @click="showData">คลิกเพื่อดูข้อมูล</button>
      <button @click="increment">เพิ่ม</button>
      <button @click="decrement">ลด</button> -->
      <!-- Event Argument -->
      <!-- <button @click="showData">คลิกเพื่อดูข้อมูล</button> -->
      <!-- <button @click="increment(10)">เพิ่ม กดปกติ</button> -->
      <!-- event modifier -->
      <!-- <button @click.ctrl="increment(10)">เพิ่ม กด ctrl + คลิกซ้าย</button> -->
      <!-- <button @click="decrement(5)">ลด</button> -->
    </article>
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
      nickname:"",
      age:27,
      address:"<strong>กรุงเทพมหานคร</strong>",
      picture:"https://t3.ftcdn.net/jpg/05/53/79/60/360_F_553796090_XHrE6R9jwmBJUMo9HKl41hyHJ5gqt9oz.jpg",
      size:150,
      social:"https://www.youtube.com",
      // Data Array 
      hobby:["เล่นกีฬา","เล่นเกมส์","ดูหนัง"],
      // Data Object
      general:{gender:"ชาย",weight:82.4,height:170,status:false},
      // ซ่อน/แสดง Element (v-show)
      isVisible:false,
      salary:20000
    }
  },
  // การอ้างอิง methods
  // ใน template ใช้ {{ ชื่อ methods }}
  // ใน script keyword:this.ชื่อ method
  methods:{
    // getFullName(){
    //   // ถ้าในพื้นที่เดียวกัน ใช้ this แต่คิดว่าถ้าเป็นการส่งข้อมูลจากอีกหน้าหนึ่งมา ไม่ต้องใช้
    //   // return this.firstname + this.lastname
    //   return `${this.firstname}  ${this.lastname}`
    // },
    // event
    showData(){
      alert(this.firstname)
    },
    // increment(){
    //   this.age++
    // },
    // decrement(){
    //   this.age--
    // }
    // event argument
    increment(value){
      this.age+=value
    },
    decrement(value){
      this.age-=value
    },
    // eventinput
    setNickname(event){
      this.nickname = event.target.value
    },
    // event modifier
    submitForm(){
      alert("บันทึกชื่อเล่นเรียบร้อยแล้ว")
      // Ref DOM Element
      console.log(this.$refs.imageEl);
      console.log(this.$refs.nicknameEl);
      this.nickname = this.$refs.nicknameEl.value;
    },
    // ซ่อน/แสดง Element (v-show)
    toggleVisible(){
      this.isVisible = !this.isVisible
    },
    getRandomByMethod(){
      return Math.random();
    },
    addSalary(value){
      this.salary += value;
    }

  },
  computed:{
    getFullName(){
      // ถ้าในพื้นที่เดียวกัน ใช้ this แต่คิดว่าถ้าเป็นการส่งข้อมูลจากอีกหน้าหนึ่งมา ไม่ต้องใช้
      // return this.firstname + this.lastname
      return `${this.firstname}  ${this.lastname}`
    },
    getRandomByComputed(){
      return Math.random();
    },
    getincome(){
      return this.salary * 12;
    },
    getDepartment(){
      return this.salary >= 35000 ? "Project Manager" : "Programmer"
    },

  }
}
</script>

<style>

</style>