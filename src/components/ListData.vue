<template>
  <ul>
    <Student
      @delete-item="onDeleteItem"
      v-for="(item, index) in studentList"
      :index="index"
      :key="item.id"
      :prename="item.prename"
      :name="item.name"
      :stuID="item.stuID"
      :faculty="item.faculty"
      :branch="item.branch"
      :subj="item.subj"
      :dateCancle="item.dateCancle"
      :dateTest="item.dateTest"
      :dueTo="item.dueTo"
    />
  </ul>
</template>

<script>
import Student from "./Student.vue";
import Swal from "sweetalert2";
export default {
  props: {
    studentList: [],
  },
  emits: ["deleteItem"],
  name: "ListData",
  methods: {
    onDeleteItem(index) {
      Swal.fire({
        title: "Do you want to save the changes?",
        showDenyButton: true,
        confirmButtonText: "Delete",
        denyButtonText: `Cancle`,
      }).then((result) => {
        /* Read more about isConfirmed, isDenied below */
        if (result.isConfirmed) {
          this.studentList.splice(index, 1);
          Swal.fire("Saved!", "", "Item had been delete");
        } else if (result.isDenied) {
          Swal.fire("Delete action got denied", "", "info");
        }
      });
    },
  },
  components: {
    Student,
  },
};
</script>

<style scoped>
ul {
  list-style: none;
  margin: 1rem 0;
}
</style>
