<template>
    <!-- <div>
        <h1>{{ message }}</h1>
    </div> -->
    <form @submit.prevent="submitForm">
        <!-- Input (v-model) -->
        <div class="form-control">
            <label for="emp-name">ชื่อพนักงาน</label>
            <input type="text" v-model.trim="employee.name"/>
        </div>
        <div class="form-control">
            <label for="emp-salary">เงินเดือน</label>
            <input type="number" v-model="employee.salary"/>
        </div>
        <!-- Input (v-model) select -->
        <div class="form-control">
            <label for="emp-department">ตำแหน่งงาน</label>
            <select v-model="employee.department">
                <option value="ลูกเรือ">ลูกเรือ</option>
                <option value="คุมเรือ">คุมเรือ</option>
                <option value="ซ่อมเรือ">ซ่อมเรือ</option>
            </select>
        </div>
        <!-- Input (v-model) radio -->
        <div class="form-control">
            <h2>เพศ</h2>
            <div>
                <input type="radio" value="ชาย" v-model="employee.gender">
                <label for="gender-name">ชาย</label>
            </div>
            <div>
                <input type="radio" value="หญิง" v-model="employee.gender">
                <label for="gender-name">หญิง</label>
            </div>
        </div>
        <!-- Input (v-model) checkbox -->
        <div class="form-control">
            <h2>ทักษะ</h2>
            <div>
                <input type="checkbox" value="ดาบ" v-model="employee.skill">
                <label for="skill">ดาบ</label>
            </div>
            <div>
                <input type="checkbox" value="ฮาคิ" v-model="employee.skill">
                <label for="skill">ฮาคิ</label>
            </div>
            <div>
                <input type="checkbox" value="วางแผน" v-model="employee.skill">
                <label for="skill">วางแผน</label>
            </div>
        </div>
        <div>
            <button>บันทึกข้อมูล</button>
        </div>
        <!-- {{ JSON.stringify(employee) }} -->
    </form>
</template>

<script>
export default {
    name:"FormComponent",
    data(){
        return{
            // message:"แบบฟอร์มสำหรับข้อมูลพนักงาน"
            employee:{
                name:"",
                salary:0,
                department:"",
                gender:"",
                skill:[]
            }
        }
    },
    methods:{
        submitForm(){
            console.log("บันทึกข้อมูลพนักงาน")
            console.log(this.employee)
        }
    }
}
</script>

<style scoped>
form{
    margin: 2rem auto;
    max-width: 40rem;
    border-radius: 12px;
    box-shadow: 0 2px 10px rgba(0, 0, 0, 0.25);
    padding: 2rem;
    background: #fff;
}
.form-control{
    margin: 0.5rem 0;
}
label{
    font-weight: bold;
}
input,select{
    display: block;
    width: 100%;
    font: inherit;
    margin-top: 0.5rem;
}
button{
    font: inherit;
    background: orange;
    color: white;
    cursor: pointer;
    padding: 0.5rem 1rem;
    border-radius: 15px;
}
input[type="radio"],input[type="checkbox"]{
    display: inline-block;
    width: auto;
    margin-right: 1rem;
}
input[type="radio"]+label,input[type="checkbox"]+label{
    font-weight: normal;
}
h2{
    font-size: 1rem;
    margin: 0.5rem 0;
}
</style>