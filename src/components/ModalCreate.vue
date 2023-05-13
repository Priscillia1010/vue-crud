<template>
  <div>
    <div class="container">
      <b-button @click="$bvModal.show('modal-scoped')" variant="success">Tambah Data</b-button>

      <b-modal id="modal-scoped">
        <template #modal-header="{ close }">
          <b-button size="sm" variant="outline-danger" @click="close()">
            X
          </b-button>
        </template>

        <template>
          <div class="form-group">
            <label for="nama sekolah">Name Sekolah</label>
            <input
              type="text"
              name="nama sekolah"
              class="form-control"
              placeholder="nama sekolah"
              v-model="nama_sekolah"
            />
          </div>

          <div class="form-group">
            <label for="tahun">Tahun</label>
            <input
              type="text"
              name="tahun"
              class="form-control"
              placeholder="tahun"
              v-model="tahun"
            />
          </div>

          <div class="form-group">
            <label for="jurusan">Jurusan</label>
            <input
              type="text"
              name="jurusan"
              class="form-control"
              placeholder="jurusan"
              v-model="jurusan"
            />
          </div>

          <div class="form-group">
            <label for="jenjang">Jenjang</label>
            <input
              type="text"
              name="jenjang"
              class="form-control"
              placeholder="jenjang"
              v-model="jenjang"
            />
          </div>
          {{ nama_sekolah }} - {{ tahun }} - {{ jurusan }} - {{ jenjang }}
        </template>

        <template #modal-footer="{  cancel }">
          <b-button size="sm" variant="success" @click.prevent="createData"> OK </b-button>
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
  name: "ModalButton",
  data() {
    return {
      nama_sekolah: "",
      tahun: "",
      jurusan: "",
      jenjang: "",
    };
  },
  methods: {
    createData() {
      axios
        .post("http://localhost:3000/pendidikan", {
          nama_sekolah: this.nama_sekolah,
          tahun: this.tahun,
          jurusan: this.jurusan,
          jenjang: this.jenjang,
        })
        .then(() => {
          alert("data berhasil ditambah")
          window.location.reload(true);
        })
        .catch(() => {
          alert("data gagal ditambah");
          window.location.reload(true);
        })
    },
  },
};
</script>
<style scoped></style>
