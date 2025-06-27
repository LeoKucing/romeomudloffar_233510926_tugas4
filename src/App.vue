<template>
  <div class="container">
    <h1>📋 Daftar Produk Kopi</h1>

    <!-- Form Tambah Produk -->
    <form @submit.prevent="tambahProduk" class="form-produk">
      <input v-model="nama" placeholder="Nama Produk" required />
      <input v-model="harga" placeholder="Harga Produk" required />
      <button type="submit">Tambah Produk</button>
    </form>

    <!-- Tabel Produk -->
    <table>
      <thead>
        <tr>
          <th>No</th>
          <th>Nama</th>
          <th>Harga</th>
          <th>Aksi</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(item, index) in daftarProduk" :key="index">
          <td>{{ index + 1 }}</td>
          <td>{{ item.nama }}</td>
          <td>{{ item.harga }}</td>
          <td>
            <button class="hapus-btn" @click="hapusProduk(index)">Hapus</button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const daftarProduk = ref([
  { nama: 'Kopi Hitam', harga: 'Rp 15.000' },
  { nama: 'Cappucino', harga: 'Rp 20.000' }
])

const nama = ref('')
const harga = ref('')

const tambahProduk = () => {
  daftarProduk.value.push({
    nama: nama.value,
    harga: harga.value
  })
  nama.value = ''
  harga.value = ''
}

const hapusProduk = (index) => {
  daftarProduk.value.splice(index, 1)
}
</script>

<style scoped>
.container {
  max-width: 700px;
  margin: 50px auto;
  padding: 25px;
  border-radius: 15px;
  background-color: #f8f9fa;
  box-shadow: 0 8px 16px rgba(0,0,0,0.1);
  text-align: center;
}

h1 {
  margin-bottom: 30px;
  color: #333;
}

.form-produk {
  display: flex;
  gap: 10px;
  justify-content: center;
  margin-bottom: 30px;
  flex-wrap: wrap;
}

input {
  padding: 8px 12px;
  border: 1px solid #ccc;
  border-radius: 8px;
  flex: 1 0 150px;
}

button {
  padding: 8px 14px;
  background-color: #4CAF50;
  color: white;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  transition: 0.3s;
}

button:hover {
  background-color: #45a049;
}

table {
  width: 100%;
  border-collapse: collapse;
  margin-top: 20px;
}

thead {
  background-color: #333;
  color: #fff;
}

th, td {
  padding: 12px 15px;
  border: 1px solid #ddd;
}

tr:nth-child(even) {
  background-color: #f2f2f2;
}

.hapus-btn {
  background-color: #e74c3c;
}

.hapus-btn:hover {
  background-color: #c0392b;
}
</style>
