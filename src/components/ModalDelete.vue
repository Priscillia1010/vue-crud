<template>
  <div>
    <div class="container">
      <b-button @click="$bvModal.show(id+'-delete')" variant="danger">Delete Data</b-button>
      <b-modal :id="id+'-delete'">
        <template #modal-header="{ close }">
          <b-button size="sm" variant="outline-danger" @click="close()">
            X
          </b-button>
        </template>

        <template>
          <h3>Are you sure want to Delete this data?</h3>
        </template>

        <template #modal-footer="{ cancel }">
          <b-button size="sm" variant="success" @click.prevent="daleteData">
            OK
          </b-button>
          <b-button size="sm" variant="danger" @click="cancel()">
            Cancel
          </b-button>
        </template>
      </b-modal>
    </div>
  </div>
</template>
<script>
import axios from "axios";
export default {
  name: "ModalDelete",
  props: [ "id"],
  methods: {
    daleteData() {
      axios
        .delete("http://localhost:3000/pendidikan/" + this.id)
        .then(() => {
          alert("data berhasil dihapus");
          window.location.reload(true);
        })
        .catch(() => {
          alert("data gagal dihapus");
          window.location.reload(true);
        });
    },
  },
};
</script>
<style scoped></style>
