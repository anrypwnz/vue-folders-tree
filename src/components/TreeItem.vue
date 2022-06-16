<template>
  <li>
    <div
        :class="{bold: isFolder}"
        class="cell"
        @click="toggle(item)"
    >
        <span v-if="isFolder">
          <img v-if="isOpen" :src="openedFolderIcon" alt="folder">
          <img v-else :src="folderIcon" alt="folder">
        </span>
      <img v-else :src="fileIcon" alt="file">
      {{ item.name }}
    </div>
    <ul v-show="isOpen" v-if="isFolder">
      <tree-item
          class="item"
          v-for="(child, index) in item.children"
          :key="index"
          :item="child"
      />
    </ul>
  </li>
</template>

<script>
import folderIcon from "@/assets/icons8-folder.svg";
import openedFolderIcon from "@/assets/icons8-opened-folder.svg";
import fileIcon from "@/assets/icons8-file.svg";

export default {
  name: "TreeItem",

  props: {
    item: Object,
  },

  data() {
    return {
      isOpen: false,
      folderIcon,
      openedFolderIcon,
      fileIcon,
    };
  },

  methods: {
    toggle(item) {
      this.$root.selected = item.name
      if (this.isFolder) {
        this.isOpen = !this.isOpen;
      }
    },
  },

  computed: {
    isFolder() {
      return this.item.children && this.item.children.length;
    },
  },
}
</script>

<style scoped>
.cell {
  cursor: pointer;
  padding: 4px 0;
  display: flex;
  align-items: center;
  gap: 8px;
}

.bold {
  font-weight: bold;
}

ul {
  list-style-type: none;
}

li {
  list-style-type: none;
}

</style>