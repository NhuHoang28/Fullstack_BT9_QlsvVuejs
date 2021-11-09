<template>
<div id="app">
    <b class="title">Danh sách sinh viên</b>
    <div class="mssv" v-for="(student,index) in Students" :key="index" @click="detail(index)">
        mssv
        {{student.id}}
        <span></span>
    </div>
    <button v-show="!add" @click="openAdd()">Thêm sinh viên</button>
    <div id="addStudent" v-show="add">
        <div>
            <span>Mssv</span>
            <input type="text" v-model="newStudent.id">
        </div>
        <div>
            <span>Name</span>
            <input type="text" v-model="newStudent.name"></div>
        <div>
            <span>Age</span>
            <input type="text" v-model="newStudent.age"></div>
        <div><span>Gender</span>
            <select name="" id="" v-model="newStudent.gender">
                <option value="male">male</option>
                <option value="female">female</option>
            </select></div>
        <div><span>Class</span>
            <input type="text" v-model="newStudent.class"></div>

        <button v-show="add" @click="addStudent()">Hoàn thành</button>
    </div>
    <student :student="showStudent" :closeDetail="closeDetail" :deleteStudent="deleteStudent" :index="index" v-show="show" />
</div>
</template>

<script>
import Student from "./Student.vue"
export default {
    data() {
        return {
            show: false,
            index: 0,
            showStudent: {},

            add: false,
            newStudent: {},
            Students: [{
                    id: 102190032,
                    name: 'Nhu',
                    age: 20,
                    gender: 'female',
                    uni: 'BKDN',
                    class: '19TCLC_DT1'
                },
                {
                    id: 102190012,
                    name: 'Nhung',
                    age: 18,
                    gender: 'female',
                    uni: 'BKDN',
                    class: '19TCLC_DT3'
                },
                {
                    id: 102190042,
                    name: 'Phuong',
                    age: 22,
                    gender: 'female',
                    uni: 'BKDN',
                    class: '19TCLC_DT2'
                },
                {
                    id: 102190030,
                    name: 'Hanh',
                    age: 24,
                    gender: 'male',
                    uni: 'BKDN',
                    class: '19TCLC_DT4'
                },
            ]
        }
    },
    components: {
        Student
    },
    methods: {
        detail(index) {
            this.showStudent = this.Students[index];
            this.show = true;
            this.index = index;
        },
        closeDetail() {
            this.show = false;
        },
        deleteStudent(index) {
            this.Students.splice(index, 1);
            this.show = false;
        },
        openAdd() {
            this.add = !this.add;
        },
        addStudent() {
            this.add = !this.add; 
            if (this.newStudent.id !=undefined) {
                
            console.log(this.newStudent.id);
                this.newStudent.age = parseInt(this.newStudent.age);
                this.newStudent.uni = "BKDN";
                this.Students.push(this.newStudent); 
            }
            this.newStudent = {};
        }
    }
}
</script>

<style scoped>
* {
    padding: 0px;
    margin: 0px;
    box-sizing: border-box;
    outline: none;
}

#app {
    width: 50%;
    height: 50%;
    background-color: rgba(0, 0, 0, 0.3);
    margin: 50px auto;
}

#app .title {
    display: block;
    text-transform: uppercase;
    height: 50px;
    line-height: 50px;
    text-align: center;
}

#app>div {
    padding: 10px;
    position: relative;
}

#app>div:nth-child(2n) {
    background-color: rgba(255, 255, 255, 0.4);
}

#app>div:nth-child(2n+1) {
    background-color: rgba(0, 0, 0, 0.2);
}

#app .mssv span {
    position: absolute;
    top: 15px;
    right: 20px;
    display: inline-block;
    width: 0px;
    height: 0px;
    border: 5px solid black;
    border-bottom-color: transparent;
    border-left-color: transparent;
    border-right-color: transparent;

}

button {
    display: block;
    margin: 10px 0px;
    margin-left: auto;
    padding: 5px;
    border-radius: 2px;
    border: 1px solid rgba(0, 0, 0, 0.3);
}

#app #addStudent {
    margin: 20px 0px;
    display: flex;
    flex-wrap: wrap;
}

#app #addStudent div {
    margin: 10px;
    display: inline-block;

}

#app #addStudent span {
    display: inline-block;
    width: 30px;
    margin: 10px 18px;
}
</style>
