<template>
<div id="detail">
    <div class="mask" @click="closeDetail()"></div>
    <div class="detail">
        MSSV <div> {{student.id}}</div>
        Name <div> {{student.name}}</div>
        Age<div> {{student.age}}</div>
        Gender<div> {{student.gender}}</div>
        University<div>{{student.uni}}</div>
        Class <div> {{student.class}}</div>
        <div class="button">
            <button @click="closeDetail()">Đóng</button>
            <button @click="deleteStudent(index)">Xóa</button>
        </div>
    </div>
</div>
</template>

<script>
 export default {
     data() {
         return {}
     },
     props: ['student', 'closeDetail', 'deleteStudent', 'index'],
     methods: {

     }
 }
</script>

<style scoped>
* {
    padding: 0px;
    margin: 0px;
    box-sizing: border-box;
}

#detail {
    height: 0px;
    background-color: red;
}

#detail .mask {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.7);
}

#detail .detail {
    display: inline-block;
    position: fixed;
    top: calc(50% - 200px);
    left: calc(50% - 150px);
    width: 400px;
    /* height:300px;   */
    background-color: white;
    border-radius: 3px;
    box-shadow: 4px 4px 2px 1px rgba(255, 255, 255, 0.2);
    background-color: rgba(255, 255, 255, 1);
    padding: 20px;
    color: black;
}

#detail .detail div {
    display: block;
    margin-bottom: 10px;
    background-color: rgba(0, 0, 0, 0.1);
    text-align: center;
    border-radius: 1px;
    padding: 3px;

}

#detail .detail .button {
    text-align: end;
    background-color: transparent;
}

#detail .detail .button button {
    display: inline-block;
    margin-left: auto;
    margin: 10px 2px 0px 2px;
    background-color: rgba(0, 0, 0, 0.1);
    padding: 5px 10px;
    border: none;
    border-radius: 2px;
}
</style>
