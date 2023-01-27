<script>
// import DocView from "./components/DocView.vue";
import ListData from "./components/ListData.vue";
import FormComponent from "./components/FormComponent.vue";
export default {
  name: "App",
  components: {
    ListData,
    FormComponent,
  },
  data() {
    return {
      student: [],
    };
  },
  methods: {
    insertStudent(data) {
      console.log("ข้อมูลนักศึกษา =", data);
      this.student.push(data);
    },
  },
};
</script>

<template>
  <header>
    <h1>คำขอเลื่อนสอบและสอบชดใช้</h1>
  </header>
  <FormComponent @save="insertStudent"></FormComponent>
  <section class="stu-content" v-if="student.length > 0">
    <h2>รายการ</h2>
    <ListData :student-list="student" />
  </section>
</template>

<style scoped>
.stu-content {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 3rem;
  border-radius: 10px;
  padding: 1rem;
  text-align: center;
}
.stu-content h2 {
  font-size: 2rem;
  border-bottom: 4px solid #ccc;
  color: blue;
  margin: 0 0 1rem 0;
}
</style>

<style>
* {
  box-sizing: border-box;
}
body {
  margin: 0;
}
header {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 3rem;
  border-radius: 10px;
  padding: 1rem;
  background-color: aliceblue;
  color: #000;
  text-align: center;
}
</style>
