<template>
  <form @submit.prevent="submitfrom">
    <div class="form-control">
      <label for="stu-name">คำนำหน้า</label>
      <div>
        <input type="radio" v-model="student.prename" value="นาย" />
        <label for="Mr.">นาย</label
        ><input type="radio" v-model="student.prename" value="นาง" />
        <label for="Mrs.">นาง</label
        ><input type="radio" v-model="student.prename" value="นางสาว" />
        <label for="Miss.">นางสาว</label>
      </div>
    </div>
    <div class="form-control">
      <label for="stu-name">ชื่อ-นามสกุล</label>
      <input type="text" v-model.trim="student.name" maxlength="100" required />
    </div>
    <div class="form-control">
      <label for="stu-ID">รหัสสนักศึกษา</label>
      <input type="text" v-model.trim="student.stuID" maxlength="10" required />
    </div>
    <div class="form-control">
      <label for="faculty">คณะ</label>
      <select v-model="student.faculty">
        <option value="">----กรุณาเลือก----</option>
        <option value="วิทยาศาสตร์">วิทยาศาสตร์</option>
        <option value="ศิลปศาสตร์">ศิลปศาสตร์</option>
        <option value="บริหาร">บริหาร</option>
        <option value="ท่องเที่ยว">ท่องเที่ยว</option>
        <option value="เกษตร">เกษตร</option>
        <option value="ประมง">ประมง</option>
      </select>
    </div>
    <div class="form-control">
      <label for="branch">สาขา</label>
      <input
        type="text"
        v-model.trim="student.branch"
        maxlength="100"
        required
      />
    </div>
    <div class="form-control">
      <label for="subj">เลื่อนสอบรายวิชา</label>
      <input type="text" v-model.trim="student.subj" maxlength="100" required />
    </div>
    <div class="form-control">
      <label for="dateCancle">ในวันที่</label>
      <div>
        <input type="datetime-local" v-model="student.dateCancle" />
      </div>
    </div>
    <div class="form-control">
      <label for="dateTest">สอบชดใช้ในวันที่</label>
      <div>
        <input type="datetime-local" v-model="student.dateTest" />
      </div>
    </div>
    <div>
      <label for="dueTo">เนื่องจาก</label>
      <input
        type="text"
        v-model="student.dueTo"
        style="margin-bottom: 0.25rem"
        maxlength="1000"
      />
    </div>
    <div>
      <button>ยืนยัน</button>
    </div>
  </form>
</template>

<script>
export default {
  name: "FormComponent",
  data() {
    return {
      student: {
        prename: "",
        name: "",
        stuID: "",
        faculty: "",
        branch: "",
        subj: "",
        dateCancle: "",
        dateTest: "",
        dueTo: "",
      },
    };
  },
  methods: {
    submitfrom() {
      console.log("Save");
      console.log(this.student);
      const newStu = {
        prename: this.student.prename,
        name: this.student.name,
        stuID: this.student.stuID,
        faculty: this.student.faculty,
        branch: this.student.branch,
        subj: this.student.subj,
        dateCancle: this.student.dateCancle,
        dateTest: this.student.dateTest,
        dueTo: this.student.dueTo,
      };
      this.$emit("save", newStu);
    },
  },
};
</script>

<style scoped>
form {
  margin: 2rem auto;
  max-width: 40rem;
  border-radius: 12px;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.25);
  padding: 2rem;
  background: #fff;
}
.form-control {
  margin: 0.5rem 0;
}
label {
  font-weight: bold;
}
input,
select {
  display: block;
  width: 100%;
  font: inherit;
  margin-top: 0.25rem;
}
button {
  font: inherit;
  background: rgb(215, 56, 56);
  color: rgb(255, 255, 255);
  padding: 0.25rem 1rem;
  border-radius: 5px;
}
input[type="radio"] {
  display: inline-block;
  width: auto;
  margin-right: 1rem;
}
input[type="radio"] + label {
  font-weight: normal;
}
input[type="date"] {
  display: block;
  width: 45%;
}
input[type="time"] {
  display: block;
  width: 45%;
}
</style>
