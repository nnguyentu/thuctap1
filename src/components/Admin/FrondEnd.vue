<template>
  <AdminLayout />
  <div>
    <table>
      <tbody>
        <tr v-for="item in items" :key="item.id" @click="showPopup(item)">
          <td>{{ item.name }}</td>
          <td>{{ item.description }}</td>
        </tr>
      </tbody>
    </table>
    <Popup :item="selectedItem" v-if="showPopupFlag" @close="closePopup" />
  </div>
</template>
<script>
import Popup from "./Popup.vue";
import AdminLayout from "./AdminLayout.vue";
export default {
  components: {
    Popup,
    AdminLayout,
  },
  data() {
    return {
      items: [
        { id: 1, name: "Item 1", description: "Description 1" },
        { id: 2, name: "Item 2", description: "Description 2" },
        { id: 3, name: "Item 3", description: "Description 3" },
      ],
      showPopupFlag: false,
      selectedItem: null,
    };
  },
  methods: {
    showPopup(item) {
      this.selectedItem = item;
      this.showPopupFlag = true;
    },
    closePopup() {
      this.selectedItem = null;
      this.showPopupFlag = false;
    },
  },
};
</script>
<style scoped></style>
