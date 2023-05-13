<template>
  <div class="container">
    <Modal></Modal>
    <Table></Table>
  </div>
</template>

<script>
import Modal from "./components/ModalCreate.vue";
import Table from "./components/TablePage.vue";
export default {
  name: "App",
  components: {
    Modal,
    Table,
  },
  created(){

  },
};
</script>

<style></style>
