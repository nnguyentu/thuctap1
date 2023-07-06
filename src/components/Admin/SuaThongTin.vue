<template>
  <div>
    <v-card-text>
      <div class="text-h2 pa-12">
        <h1 style="margin-left: -30px; font-size: xx-large">
          Cập nhật người dùng
        </h1>
      </div>
      <img
        class="avatar-custom"
        src="https://demoda.vn/wp-content/uploads/2022/01/anh-dai-dien-nguoi-giau-mat.jpg"
        alt="avatar"
      />

      <p style="color: gray; margin-left: 2%; margin-bottom: 1%">
        Anh đại diện người dùng
      </p>
      <v-btn style="background-color: aqua; margin-left: 2%; margin-bottom: 1%">
        chọn ảnh
      </v-btn>
      <div class="tf1-custom">
        <div class="textfied1-custom">
          <v-text-field
            v-model="selectedItem.hai"
            label="Phật tử"
            placeholder="Placeholder"
            variant="outlined"
          ></v-text-field>
        </div>
        <div class="textfied1-custom">
          <v-text-field
            label="khóa học"
            placeholder="Placeholder"
            variant="outlined"
          ></v-text-field>
        </div>
        <div class="textfied1-custom">
          <!-- <v-text-field
            label="dd/mm/yyyy"
            placeholder="Placeholder"
            variant="outlined"
            >
          </v-text-field> -->
          <input
            style="
              border: 1px solid black;
              height: 56px;
              text-align: center;
              border-color: rgba(128, 128, 128, 0.466);
              border-radius: 4px;
              color: gray;
            "
            type="datetime-local"
            id="meeting-time"
            name="meeting-time"
          />
          <v-container>
            <v-row justify="space-around">
              <v-date-picker elevation="24"></v-date-picker>
            </v-row>
          </v-container>
        </div>
      </div>

      <div class="tf2-custom">
        <div class="textfied2-custom">
          <v-text-field
            label="Lớp học"
            placeholder="Placeholder"
            variant="outlined"
          ></v-text-field>
        </div>
        <div class="textfied2-custom">
          <v-text-field
            label="Số buổi đạo tràng đã tham gia"
            placeholder="Placeholder"
            variant="outlined"
          ></v-text-field>
        </div>
        <div class="textfied2-custom">
          <v-text-field
            label="Số điện thoại"
            placeholder="Placeholder"
            variant="outlined"
          ></v-text-field>
        </div>
      </div>
      <div class="tf3-custom">
        <div class="textfied3-custom">
          <v-text-field
            label="Tên tài khoản"
            placeholder="Placeholder"
            variant="outlined"
          ></v-text-field>
        </div>
        <div class="textfied3-custom">
          <v-text-field
            v-model="bay"
            label="E-mail"
            placeholder="Placeholder"
            variant="outlined"
          ></v-text-field>
        </div>
        <div class="textfied3-custom">
          <v-text-field
            label="Mật khẩu"
            placeholder="Placeholder"
            variant="outlined"
          ></v-text-field>
        </div>
      </div>
      <div class="tf4-custom" style="margin-left: 1%; border-bottom: unset">
        <v-container fluid>
          <v-textarea
            style="margin-left: -5px"
            label="Địa chỉ hiện tại"
            auto-grow
            variant="outlined"
            rows="5"
            row-height="25"
            shaped
          ></v-textarea>
        </v-container>
      </div>
      <div class="select-custom">
        <div class="select1-custom">
          <v-select
            label="Tỉnh/Thành phố"
            :items="[]"
            variant="outlined"
          ></v-select>
        </div>
        <div class="select1-custom">
          <v-select
            label="Quận/huyện"
            :items="[]"
            variant="outlined"
          ></v-select>
        </div>
        <div class="select1-custom">
          <v-select label="Xã/phường" :items="[]" variant="outlined"></v-select>
        </div>
      </div>
      <div class="select2-custom">
        <div class="select3-custom">
          <v-select
            label="Giới tính"
            :items="['nam', 'nữ']"
            variant="outlined"
          ></v-select>
        </div>
        <div class="select3-custom">
          <v-select
            label="Công việc hiện tại"
            :items="[]"
            variant="outlined"
          ></v-select>
        </div>
        <div class="select3-custom">
          <v-select
            label="Thành viên"
            :items="[]"
            variant="outlined"
          ></v-select>
        </div>
      </div>
    </v-card-text>

    <!-- <v-card-title>
      <span class="text-h5">User Profile</span>
    </v-card-title>
    <v-card-text>
      <v-container>
        <v-row>
          <v-col cols="12" sm="6" md="4">
            <v-text-field label="Legal first name*" required></v-text-field>
          </v-col>
          <v-col cols="12" sm="6" md="4">
            <v-text-field
              label="Legal middle name"
              hint="example of helper text only on focus"
            ></v-text-field>
          </v-col>
          <v-col cols="12" sm="6" md="4">
            <v-text-field
              label="Legal last name*"
              hint="example of persistent helper text"
              persistent-hint
              required
            ></v-text-field>
          </v-col>
          <v-col cols="12">
            <v-text-field label="Email*" required></v-text-field>
          </v-col>
          <v-col cols="12">
            <v-text-field
              label="Password*"
              type="password"
              required
            ></v-text-field>
          </v-col>
          <v-col cols="12" sm="6">
            <v-select
              :items="['0-17', '18-29', '30-54', '54+']"
              label="Age*"
              required
            ></v-select>
          </v-col>
          <v-col cols="12" sm="6">
            <v-autocomplete
              :items="[
                'Skiing',
                'Ice hockey',
                'Soccer',
                'Basketball',
                'Hockey',
                'Reading',
                'Writing',
                'Coding',
                'Basejump',
              ]"
              label="Interests"
              multiple
            ></v-autocomplete>
          </v-col>
        </v-row>
      </v-container>
      <small>*indicates required field</small>
    </v-card-text> -->
  </div>
  <div>
    <button @click="updateChildData"></button>
    <child-component
      :HienThiChiTiet="HienThiChiTiet"
      @data-updated="onDataUpdated"
    />
  </div>
</template>
<script>
export default {
  props: { favorite_count: Number },
  data() {
    return {
      dialog: false,
      Infos: [
        { title: "Họ tên" },
        { title: "Pháp danh" },
        { title: "Số điện thoại" },
        { title: "Email" },
        { title: "Kiểu thành viên" },
      ],
      childData: "HienThiChiTiet",
    };
  },
  methods: {
    updateChildData() {
      // Thay đổi dữ liệu trong component cha
      this.HienThiChiTiet = "Updated child data";
    },
    onDataUpdated(updatedData) {
      // Xử lý sự kiện dữ liệu được cập nhật từ component con
      console.log("Data updated in parent component:", updatedData);
    },
  },
};
</script>
<style scoped>
.avatar-custom {
  width: 100px;
  height: 100px;
  margin-left: 2%;
  margin-bottom: 1%;
}

.select-custom {
  display: flex;
  justify-content: flex-start;
}
.select1-custom {
  margin-left: 2%;
  width: 31%;
}
.select2-custom {
  display: flex;
  justify-content: flex-start;
}
.select3-custom {
  margin-left: 2%;
  width: 31%;
}
.tf1-custom {
  display: flex;
  justify-content: flex-start;
}
.tf2-custom {
  display: flex;
  justify-content: flex-start;
}
.tf3-custom {
  display: flex;
  justify-content: flex-start;
}
.textfied1-custom {
  margin-left: 2%;
  width: 31%;
}
.textfied2-custom {
  margin-left: 2%;
  width: 31%;
}
.textfied3-custom {
  margin-left: 2%;
  width: 31%;
}
:deep(.v-field--variant-filled .v-field__outline::before) {
  border-bottom: unset;
}
:deep(.tf1-custom .v-field__outline) {
  border-color: rgba(128, 128, 128, 0.466);
}
:deep(.tf2-custom .v-field__outline) {
  border-color: rgba(128, 128, 128, 0.466);
}
:deep(.tf4-custom .v-field__outline) {
  /* border-style: solid;
  border-width: 1px;
  border-color: rgba(128, 128, 128, 0.466);
  background-color: white; 
  text-decoration-color: black; */
}
</style>
