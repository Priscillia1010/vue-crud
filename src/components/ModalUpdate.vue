<template>
  <div>
    <div class="container">
      <b-button @click="$bvModal.show(id)">Update Data</b-button>
      <b-modal :id="id">
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
              v-model="nama_sekolah_data"
            />
          </div>

          <div class="form-group">
            <label for="tahun">Tahun</label>
            <input
              type="text"
              name="tahun"
              class="form-control"
              placeholder="tahun"
              v-model="tahun_data"
            />
          </div>

          <div class="form-group">
            <label for="jurusan">Jurusan</label>
            <input
              type="text"
              name="jurusan"
              class="form-control"
              placeholder="jurusan"
              v-model="jurusan_data"
            />
          </div>

          <div class="form-group">
            <label for="jenjang">Jenjang</label>
            <input
              type="text"
              name="jenjang"
              class="form-control"
              placeholder="jenjang"
              v-model="jenjang_data"
            />
          </div>
          {{ id }} - {{ nama_sekolah_data }} - {{ tahun }} - {{ jurusan }} -
          {{ jenjang }}
        </template>

        <template #modal-footer="{ cancel }">
          <b-button size="sm" variant="success" @click.prevent="updateData">
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
  name: "ModalCreate",
  props: ["nama_sekolah", "id", "tahun", "jurusan", "jenjang"],
  data() {
    return {
      nama_sekolah_data: this.nama_sekolah,
      tahun_data: this.tahun,
      jurusan_data: this.jurusan,
      jenjang_data: this.jenjang,
    };
  },
  methods: {
    updateData() {
      axios
        .put("http://localhost:3000/pendidikan/" + this.id, {
          nama_sekolah: this.nama_sekolah_data,
          tahun: this.tahun_data,
          jurusan: this.jurusan_data,
          jenjang: this.jenjang_data,
        })
        .then(() => {
          alert("data berhasil diupdate");
          window.location.reload(true);
        })
        .catch(() => {
          alert("data gagal ditambah");
          window.location.reload(true);
        });
    },
  },
};
</script>
<style scoped></style>
