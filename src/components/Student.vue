<template>
  <Card>
    <template v-slot:card-header>
      <p>
        {{ prename }} {{ name }} รหัสนักศึกษา : {{ stuID }} คณะ :
        {{ faculty }} สาขา :{{ branch }} เลื่อนสอบรายวิชา : {{ subj }} ในวันที่
        : {{ dateCancle }} สอบชดใช้วันที่ : {{ dateTest }} เนื่องจาก :
        {{ dueTo }}
      </p>
    </template>
    <template v-slot:card-button>
      <button @click="deleteStudent(index)">ลบข้อมูล</button></template
    >
  </Card>
</template>

<script>
import Card from "./Card.vue";

export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: "Student",
  emits: ["deleteItem"],
  props: {
    prename: {
      type: String,
    },
    index: Number,
    name: {
      type: String,
      required: true,
    },
    stuID: {
      type: String,
      required: true,
    },
    branch: {
      type: String,
      required: true,
    },
    faculty: {
      type: String,
      required: true,
    },
    subj: {
      type: String,
      required: true,
    },
    dateCancle: {
      type: Date,
    },
    dateTest: {
      type: Date,
    },
    dueTo: {
      type: String,
    },
  },
  mounted() {
    console.log(this.timeCancle, this.timeTest);
  },
  methods: {
    deleteStudent(i) {
      this.$emit("deleteItem", i);
    },
  },
  components: { Card },
};
</script>

<style scoped>
button {
  font: inherit;
  cursor: pointer;
  border: 1px solid #ff0077;
  background: #ff0077;
  color: white;
  padding: 0.05rem 1rem;
  box-shadow: 1px 1px 2px rgba(0, 0, 0, 0.26);
}
.fade-enter-from {
  opacity: 0;
}
.fade-enter-active {
  transition: all 0.25s linear;
}
</style>
