<template v-slot:body="{}">
  <div class="hienthi">
    <div class="p1">
      <div class="p2">
        <v-select
          class="p5"
          label="Hiển thị 1 - 25 of 314"
          :items="[1, 2, 3, 4, 5, 7]"
          onclick="javascript:location.href''"
        >
        </v-select>
      </div>

      <v-text-field
        class="p3"
        :loading="loading"
        density="compact"
        variant="solo"
        append-inner-icon="mdi-magnify"
        single-line
        hide-details
        @click:append-inner="onClick"
        label="Tìm kiếm"
      ></v-text-field>
      <v-select class="p4" label="Sắp xếp" :items="[]"> </v-select>
    </div>
    <div id="app">
      <v-data-table
        v-model:items-per-page="itemsPerPage"
        :headers="headers"
        :items="items"
        item-value="key"
        class="elevation-1 table-custom-style"
      >
        <!-- <template v-slot:item.actions="{ item }">
          <v-icon size="small" class="me-2" @click="editItem(item.raw)">
            mdi-pencil
          </v-icon>
          <v-icon size="small" @click="deleteItem(item.raw)">
            mdi-delete
          </v-icon>
        </template> -->
        <!-- <template v-slot:no-data>
          <v-btn color="primary" @click="initialize"> Reset </v-btn>
        </template> -->

        <template v-slot:item="{ item }">
          <!-- <tr class="table-custom tr-custom-style" @click="showPopup(item)"> -->
          <tr class="table-custom tr-custom-style">
            <td style="text-align: center" class="cotmot-custom">
              {{ item.columns.mot }}
            </td>
            <td
              class="cothai-custom"
              style="display: flex; justify-items: flex-start; padding: 4px"
            >
              <v-row justify="space-around">
                <v-col cols="auto">
                  <v-dialog transition="dialog-bottom-transition" width="80%">
                    <template v-slot:activator="{ props }">
                      <div class="avatar-border">
                        <v-avatar
                          style="size: 32; -ms-grid-column-align: center"
                        >
                          <v-btn>
                            <v-img
                              v-bind="props"
                              :src="
                                item.linkAnhCaNhan
                                  ? HOST +
                                    '/api/fileupload/download/' +
                                    item.linkAnhCaNhan
                                  : 'https://demoda.vn/wp-content/uploads/2022/01/anh-dai-dien-nguoi-giau-mat.jpg'
                              "
                            ></v-img>
                          </v-btn>
                        </v-avatar>
                      </div>
                    </template>
                    <template v-slot:default="{ isActive }">
                      <v-card>
                        <v-toolbar
                          color="primary"
                          title="Opening from the bottom"
                        ></v-toolbar>
                        <div>
                          <v-card-text>
                            <div class="text-h2 pa-12">
                              <h1
                                style="margin-left: -30px; font-size: xx-large"
                              >
                                Cập nhật người dùng
                              </h1>
                            </div>
                            <img
                              class="avatar-custom"
                              src="https://demoda.vn/wp-content/uploads/2022/01/anh-dai-dien-nguoi-giau-mat.jpg"
                              alt="avatar"
                            />

                            <p
                              style="
                                color: gray;
                                margin-left: 2%;
                                margin-bottom: 1%;
                              "
                            >
                              Anh đại diện người dùng
                            </p>
                            <v-btn
                              style="
                                background-color: aqua;
                                margin-left: 2%;
                                margin-bottom: 1%;
                              "
                            >
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
                                    <v-date-picker
                                      elevation="24"
                                    ></v-date-picker>
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
                            <div
                              class="tf4-custom"
                              style="margin-left: 1%; border-bottom: unset"
                            >
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
                                <v-select
                                  label="Xã/phường"
                                  :items="[]"
                                  variant="outlined"
                                ></v-select>
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
                        <v-card-actions class="justify-end">
                          <v-btn variant="text" @click="isActive.value = false"
                            >Close</v-btn
                          >
                        </v-card-actions>
                      </v-card>
                    </template>
                  </v-dialog>
                </v-col>
              </v-row>

              <v-hover>
                <template v-slot:default="{ isHovering, props }">
                  <v-card
                    v-bind="props"
                    :color="isHovering ? 'custom-hover' : undefined"
                  >
                    {{ item.columns.hai }}
                    {{ item.raw.bay }}
                  </v-card>
                </template>
              </v-hover>

              <!-- {{ item.columns.hai }} -->
            </td>
            <td style="text-align: center" class="cotba-custom">
              {{ item.columns.ba }}
            </td>
            <td style="text-align: center" class="cotbon-custom">
              {{ item.columns.bon }}
            </td>
            <td style="text-align: center" class="cotnam-custom">
              {{ item.columns.nam }}
            </td>
            <td style="text-align: center" class="cotsau-custom">
              <!-- <v-row justify="center">
                <v-dialog v-model="dialog" persistent width="">
                  <template v-slot:activator="{ props }">
                    <v-btn color="primary" v-bind="props"> Edit </v-btn>
                  </template>
                  <v-card>
                    <SuaThongTin />
                    <v-card-actions>
                      <v-spacer></v-spacer>
                      <v-btn
                        color="blue-darken-1"
                        variant="text"
                        @click="dialog = false"
                      >
                        Close
                      </v-btn>
                      <v-btn
                        color="blue-darken-1"
                        variant="text"
                        @click="dialog = false"
                      >
                        Save
                      </v-btn>
                    </v-card-actions>
                  </v-card>
                </v-dialog>
              </v-row> -->
              <v-row justify="space-around">
                <v-col cols="auto">
                  <v-dialog transition="dialog-bottom-transition" width="80%">
                    <template v-slot:activator="{ props }">
                      <v-btn
                        style="height: 32px; width: 32px"
                        v-bind="props"
                        class="ma-2"
                        color="purple"
                        icon="mdi-wrench"
                      ></v-btn>
                    </template>
                    <template v-slot:default="{ isActive }">
                      <v-card>
                        <v-toolbar
                          color="primary"
                          title="Opening from the bottom"
                        ></v-toolbar>
                        <div>
                          <v-card-text>
                            <div class="text-h2 pa-12">
                              <h1
                                style="margin-left: -30px; font-size: xx-large"
                              >
                                Cập nhật người dùng
                              </h1>
                            </div>
                            <img
                              class="avatar-custom"
                              src="https://demoda.vn/wp-content/uploads/2022/01/anh-dai-dien-nguoi-giau-mat.jpg"
                              alt="avatar"
                            />

                            <p
                              style="
                                color: gray;
                                margin-left: 2%;
                                margin-bottom: 1%;
                              "
                            >
                              Anh đại diện người dùng
                            </p>
                            <v-btn
                              style="
                                background-color: aqua;
                                margin-left: 2%;
                                margin-bottom: 1%;
                              "
                            >
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
                                    <v-date-picker
                                      elevation="24"
                                    ></v-date-picker>
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
                            <div
                              class="tf4-custom"
                              style="margin-left: 1%; border-bottom: unset"
                            >
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
                                <v-select
                                  label="Xã/phường"
                                  :items="[]"
                                  variant="outlined"
                                ></v-select>
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
                        <v-card-actions class="justify-end">
                          <v-btn variant="text" @click="isActive.value = false"
                            >Close</v-btn
                          >
                        </v-card-actions>
                      </v-card>
                    </template>
                  </v-dialog>
                </v-col>
              </v-row>
              {{ item.columns.sau }}
            </td>
          </tr>
        </template>
      </v-data-table>
    </div>
  </div>
  <p>{{ HienThiChiTiet }}</p>
  <!-- <div>
    <table>
      <tbody>
        <tr v-for="item in items" :key="item.id" @click="showPopup(item)">
          <td>{{ item.name }}</td>
          <td>{{ item.description }}</td>
        </tr>
      </tbody>
    </table>
    <Popup :item="selectedItem" v-if="showPopupFlag" @close="closePopup" />
  </div> -->
  <div>
    <!-- <table>
      <tbody>
        <tr v-for="item in items" :key="item.id" @click="showPopup(item)">
          <td>{{ item.mot }}</td>
          <td>{{ item.hai }}</td>
          <td>{{ item.ba }}</td>
          <td>{{ item.bon }}</td>
          <td>{{ item.nam }}</td>
          <td>{{ item.bay }}</td>
        </tr>
      </tbody>
    </table> -->
    <div v-if="showPopupFlag" class="popup">
      <div class="popup-content">
        <p>{{ selectedItem.raw.mot }}</p>
        <p>{{ selectedItem.raw.hai }}</p>
        <p>{{ selectedItem.raw.ba }}</p>
        <p>{{ selectedItem.raw.bon }}</p>
        <p>{{ selectedItem.raw.nam }}</p>
        <p>{{ selectedItem.raw.bay }}</p>

        <button @click="closePopup">Close</button>
      </div>
    </div>
  </div>
</template>

<script>
import Auth from "../../api/AuthAPI/Auth";
// import SuaThongTin from "./SuaThongTin.vue";

export default {
  methods: {
    async getData() {
      const data = await Auth.getPhatTu();
      console.log(data);
      this.desserts = data.contents;
    },
    onClick() {
      this.loading = true;

      setTimeout(() => {
        this.loading = false;
        this.loaded = true;
      });
    },
    // emitDataUpdated() {
    //   // Gửi sự kiện thông báo dữ liệu đã được cập nhật từ component con lên cha
    //   this.$emit("data-updated", this.HienThiChiTiet);
    // },
    // mounted() {
    //   // Lắng nghe sự kiện khi dữ liệu trong component con thay đổi và gửi thông báo lên cha
    //   // this.$watch("HienThiChiTiet", () => {
    //   //   this.emitDataUpdated();
    //   // });
    // },
    showPopup(item) {
      this.selectedItem = item;
      this.showPopupFlag = true;
    },
    closePopup() {
      this.selectedItem = null;
      this.showPopupFlag = false;
    },
  },

  // components: { SuaThongTin },

  data() {
    return {
      // items: [
      //  {
      //     mot: "1",

      //     hai: " Nguyễn Văn A abc@gmail.com",
      //     ba: "01/01/2023",
      //     bon: "8686868686",
      //     nam: 1,
      //   },
      //   { id: 2, name: "hai", description: "Description 2" },
      //   { id: 3, name: "ba", description: "Description 3" },
      //   { id: 3, name: "bon", description: "Description 3" },
      //   { id: 3, name: "nam", description: "Description 3" },
      // ],
      favorite_count: 0,
      showPopupFlag: false,
      selectedItem: null,
      //   SuaThongTinprops: false,

      // items: SuaThongTin,
      itemsPerPage: 3,

      headers: [
        {
          title: "STT",
          align: "center",
          key: "mot",
          sortable: false,
          width: "5%",
        },

        { title: "Phật tử", align: "center", key: "hai" },
        { title: "Ngày xuất gia", align: "center", key: "ba" },
        { title: "Số điện thoại", align: "center", key: "bon" },
        {
          title: "Số buổi đạo tràng đã tham gia",
          align: "center",
          key: "nam",
        },
        { title: "Thông tin", align: "center", key: "sau", width: "10%" },
      ],

      items: [
        {
          mot: "1",

          hai: " Nguyễn Văn A ",
          bay: "abc@gmail.com",
          ba: "01/01/2023",
          bon: "8686868686",
          nam: 1,
        },
        {
          mot: "2",

          hai: "Nguyễn Văn B ",
          bay: "abc@gmail.com",
          ba: "02/01/2023",
          bon: "6868686868",
          nam: 1,
        },
        {
          mot: "3",

          hai: "Nguyễn Văn C ",
          bay: "abc@gmail.com",
          ba: "02/01/2023",
          bon: "6868686868",
          nam: 1,
        },
      ],
      // itemKey: "id", // Unique identifier for table items
      // loading: false, // Loading state
      totalItems: 3, // Total number of items
      serverItemsLength: 1, // Number of items on the server
      dialog: false,
      loaded: false,
      loading: false,
    };
  },
  // components: { SuaThongTin },
};
</script>
<style scoped>
.bg-custom-hover {
  background: none;
  color: red;
  box-shadow: none;
}
:deep(.v-theme--light) {
  box-shadow: none;
}
.hienthi {
  height: 50%;
  background-color: white;
  margin-top: 2%;
  margin-left: 2%;
  margin-right: 2%;
}
.p1 {
  display: flex;
  justify-content: flex-start;
}
.p2 {
  margin-right: 40%;
  margin-top: 2%;
  margin-left: 2%;
  width: 21%;
}

.p3 {
  margin-top: 2%;
  width: 10%;
  height: 70px;
}
.p4 {
  margin-top: 2%;
  color: red;
  background-color: white;
  width: 0%;
}
:deep(.p5 .v-field) {
  border-radius: 30px;
  border-style: solid;
  border-width: thin;
  border-color: gray;
}

:deep(.p5 .v-field--variant-filled .v-field__outline::before) {
  border-bottom: none;
}
:deep(.p5 .v-field--variant-filled .v-field__overlay) {
  color: white;
}
:deep(.p4 .v-field) {
  border: none;
}
:deep(.p4 .v-field--variant-filled .v-field__overlay) {
  color: white;
}
:deep(.p4 .v-field--variant-filled .v-field__outline::before) {
  border-bottom: none;
}
:deep(.v-table__wrapper) {
  border-style: solid;
  border-width: thin;
  border-color: gray;
  margin-left: 2%;
  margin-right: 2%;
  border-collapse: collapse;
}
.avatar-custom {
  width: 100px;
  height: 100px;
}
.text-center {
}
.anh-custom {
  color: gray;
}
tr,
td,
headers {
  border-spacing: 11px;
}
.reset-custom {
  text-align: center;
}

.table-custom-style :deep(.v-table__wrapper) {
  border: 1px solid gray !important;
}
.table-custom-style :deep(th),
.table-custom-style :deep(td) {
  border-right: 1px solid gray !important;
}
.table-custom-style tr:not(:last-child) :deep(td),
.table-custom-style :deep(th) {
  border-bottom: 1px solid gray !important;
}
/* .table-custom-style :deep(td) {
  padding: center;
} */
.popup {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  justify-content: center;
  align-items: center;
}

.popup-content {
  background-color: #fff;
  padding: 20px;
  border-radius: 5px;
}
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
</style>
