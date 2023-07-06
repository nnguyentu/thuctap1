<template>
  <NavsBar />
  <HeaderAdmin />
  <div id="admin-body">
    <router-view />
    <GiamSatHocTap />
    <TimKiem />
    <HienThiChiTiet />
  </div>
  <div v-for="post in posts" :key="post.id">post id: {{ post.id }}</div>
  <div>
    <input type="text" placeholder="Your name" v-model="name" />
    {{ name }}
  </div>
  <!-- <tbody>
    <tr v-for="(item, index) in dsGiamSat" :key="index">
      <td class="text-center" style="min-width: 110px; width: 110px">
        <v-tooltip top>
          <template v-slot:activator="{ on, attrs }">
            <v-btn
              color="primary"
              icon
              v-bind="attrs"
              v-on="on"
              @click="showModalThemSua(true, item.hocVienId)"
              class="mx-1 bg-button"
            >
              <v-icon size="22">mdi-account-box</v-icon>
            </v-btn>
          </template>
          <span>Xem thông tin cá nhân</span>
        </v-tooltip>
        <v-tooltip top>
          <template v-slot:activator="{ on, attrs }">
            <v-btn
              color="primary"
              icon
              v-bind="attrs"
              v-on="on"
              class="mx-1 bg-button"
              :to="`/giamsat/hocvien/${item.hocVienId}/khoahoc/${item.id}`"
            >
              <v-icon size="22">mdi-view-list</v-icon>
            </v-btn>
          </template>
          <span>Review</span>
        </v-tooltip>
      </td>
      <td style="width: 220px">
        <div class="box-info-hocvien my-2 d-flex align-center">
          <div class="avatar-border">
            <v-avatar size="42">
              <v-img
                :src="
                  item.linkAnhCaNhan
                    ? HOST + '/api/fileupload/download/' + item.linkAnhCaNhan
                    : '/static/img/default-avatar.png'
                "
              ></v-img>
            </v-avatar>
          </div>
          <div class="inner-box-info ml-2">
            <router-link
              :to="`/giamsat/hocvien/${item.hocVienId}/khoahoc/${item.id}`"
              class="mb-0 inner-box-info__name text-decoration--none"
              >{{ item.tenHocVien ? item.tenHocVien : "Lotusian" }}</router-link
            >
            <p class="mb-0 inner-box-info__account">
              {{ item.account ? item.account : "" }}
            </p>
          </div>
        </div>
      </td>
      <td class="text-center">{{ item.tenKhoaHoc }}</td>
      <td class="text-center">{{ item.tenLopHoc }}</td>
      <td class="text-center">{{ item.soBaiDaLam }}</td>
      <td style="width: 330px">
        <div class="d-flex justify-space-around">
          <v-tooltip top>
            <template v-slot:activator="{ on, attrs }">
              <v-chip
                dark
                class="mx-1"
                v-bind="attrs"
                v-on="on"
                color="#FFBA68"
              >
                <v-icon left>mdi-spin mdi-loading</v-icon>
                <b>{{ item.soBaiDoi }}</b>
              </v-chip>
            </template>
            <span>Bài đợi</span>
          </v-tooltip>
          <v-tooltip top>
            <template v-slot:activator="{ on, attrs }">
              <v-chip
                v-bind="attrs"
                v-on="on"
                dark
                class="mx-1"
                color="#FF9B8A"
              >
                <v-icon left>mdi-close</v-icon>
                <b>{{ item.soBaiSai }}</b>
              </v-chip>
            </template>
            <span>Bài sai</span> </v-tooltip
          ><v-tooltip top>
            <template v-slot:activator="{ on, attrs }">
              <v-chip
                v-bind="attrs"
                v-on="on"
                dark
                class="mx-1"
                color="#1ee58e"
              >
                <v-icon left>mdi-check</v-icon>
                <b>{{ item.soBaiDung }}</b>
              </v-chip>
            </template>
            <span>Bài đúng</span> </v-tooltip
          ><v-tooltip top>
            <template v-slot:activator="{ on, attrs }">
              <v-chip v-bind="attrs" v-on="on" class="mx-1">
                <v-icon left>mdi-circle-off-outline</v-icon>
                <b>{{ item.soBaiChuaLam }}</b>
              </v-chip>
            </template>
            <span>Bài chưa làm</span>
          </v-tooltip>
        </div>
      </td>
    </tr>
  </tbody> -->
</template>

<script>
import NavsBar from "./NavsBar.vue";
import HeaderAdmin from "./HeaderAdmin.vue";
import GiamSatHocTap from "./GiamSatHocTap.vue";
import TimKiem from "./TimKiem.vue";
import HienThiChiTiet from "./HienThiChiTiet.vue";
import AuthAPI from "../../api/AuthAPI/Auth";

export default {
  name: "AdminLayout",
  data() {
    return {
      name: "content",
    };
  },
  components: {
    NavsBar,
    HeaderAdmin,
    GiamSatHocTap,
    TimKiem,
    HienThiChiTiet,
  },

  methods: {
    async getData() {
      const data = await AuthAPI.getPhatTu();
      console.log(data);
    },
  },
};
</script>

<style lang="css" scoped>
#admin-body {
  margin-left: 18.75%;
  width: 80%;
  margin-top: 104px;
  min-height: 100vh;
  background-color: rgba(255, 192, 203, 0.575);
}
</style>
