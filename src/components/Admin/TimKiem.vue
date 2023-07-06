<template>
  <div class="search">
    <p class="pp">Tìm kiếm phật tử</p>
    <div class="select">
      <div class="tk">
        <p>Pháp danh</p>
        <v-select label="Tất cả" :items="[]" variant="outlined"></v-select>
      </div>
      <div class="tk">
        <p>Giới tính</p>
        <v-select label="Tất cả" :items="[]" variant="outlined"></v-select>
      </div>
      <div class="tk">
        <p>Trạng thái phật tử</p>
        <v-select label="Tất cả" :items="[]" variant="outlined"></v-select>
      </div>
    </div>
  </div>
</template>
<script></script>
<style scoped>
.search {
  background-color: white;
  margin: 2%;
}
.select {
  display: flex;
  justify-content: flex-start;
}
.tk {
  width: 100%;
  margin: 2%;
  height: 20%;
}
.pp {
  width: 100%;
  justify-content: flex-start;
  margin-left: 2%;
  padding-top: 2%;
}
</style>
