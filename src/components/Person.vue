<template>
    <!-- <li> -->
        <!-- Props (Parent to Children) -->
        <!-- <h1>ชื่อ : {{ name }} เงินเดือน : {{ salary }}</h1> -->
        <!-- <h1>ชื่อ : {{ name }}</h1> -->
        <!-- Custom Event (Children to Parent) -->
        <!-- <button @click="showDescription(id)">ดูรายละเอียด</button> &nbsp; -->
        <!-- Custom Event (ลบข้อมูล) -->
        <!-- <button @click="deleteeEmployee(id)">ลบข้อมูลพนักงาน</button> -->
        <!-- <div v-show="isVisible">
            <p>เงินเดือน : {{ salary }} , ตำแหน่งงาน : {{ department }}</p>
        </div> -->
        <!-- Transition -->
        <!-- <transition name="fade">
            <div v-show="isVisible">
                <p>เงินเดือน : {{ salary }} , ตำแหน่งงาน : {{ department }}</p>
            </div>
        </transition> -->
    <!-- </li> -->
    
    <!-- Slots -->
    <Card>
        <!-- <h1>ชื่อ : {{ name }}</h1>
            Custom Event (Children to Parent)
        <button @click="showDescription(id)">ดูรายละเอียด</button> &nbsp;
            Custom Event (ลบข้อมูล)
        <button @click="deleteeEmployee(id)">ลบข้อมูลพนักงาน</button>
        <transition name="fade">
            <div v-show="isVisible">
                <p>เงินเดือน : {{ salary }} , ตำแหน่งงาน : {{ department }}</p>
            </div>
        </transition> -->

        <!-- Named Slots -->
        <template v-slot:card-header>
            <h1>ชื่อ : {{ name }}</h1>
        </template>
        <!-- <template v-slot:card-button>
            <button @click="showDescription(id)">ดูรายละเอียด</button> &nbsp;
            <button @click="deleteeEmployee(id)">ลบข้อมูลพนักงาน</button>
        </template> -->
        <template v-slot:card-content>
            <!-- <transition name="fade"> -->
                <!-- <div v-show="isVisible"> -->
                    <p>เงินเดือน : {{ salary }} , ตำแหน่งงาน : {{ department }}</p>
                    <p>เพศ : {{ gender }} , ทักษะ : {{ skill }}</p>
                <!-- </div> -->
            <!-- </transition> -->
        </template>
    </Card>
</template>

<script>
import Card from './Card.vue';
export default {
    name:"Person",
    data(){
        return{
            message:"ข้อมูลพนักงานแต่ละคน"
        }
    },
    components:{
        Card
    },
    // Props (Parent to Children)
    // props:["name","salary"]
    // Props Validation
    props:{
        id:{
            type:Number
        },
        name:{
            type:String,
            required:true
        },
        salary:{
            type:Number,
            default:5000
        },
        department:{
            type:String,
            required:true
        },
        // isVisible:{
        //     type:Boolean,
        //     required:true
        // }
        gender:{
            type:String
        },
        skill:{
            type:Array
        }
    }//,
    // Custom Event (Children to Parent)
    // methods:{
        // Custom Event (Children to Parent)
        // showDescription(id){
        //     console.log(id);
        //     this.$emit("show",id);
        // },
        // Custom Event (ลบข้อมูล)
    //     deleteeEmployee(id){
    //         console.log(id);
    //         this.$emit("delete",id);
    //     }
    // }
}
</script>

<!-- Style Scoped -->
<style scoped>
    /* h1{
        color: red;
    } */
    /* li{
        margin: 1rem 0;
        font-size: 1.25rem;
        font-weight: bold;
        background: #8ddba4;
        padding: 0.5rem;
        color: #1f1f1f;
        border-radius: 25px;
    } */
    button{
        font: inherit;
        cursor: pointer;
        border: 1px solid #ff0077;
        background: #ff0077;
        color: white;
        padding: 0.05rem 1rem;
        box-shadow: 1px 1px 2px rgba(0, 0, 0, 0.26);
    }
    /* Transition */
    .fade-enter-from,
    .fade-leave-to{
        opacity: 0;
    }
    .fade-enter-active,
    .fade-leave-active{
        transition: all 0.5s linear;
    }
</style>