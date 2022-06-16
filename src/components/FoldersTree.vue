<template>
  <ul class="parent">
    <tree-item
        :item="data"
    />
  </ul>
</template>

<script>
import TreeItem from "@/components/TreeItem";

export default {
  name: "FoldersTree",
  components: {TreeItem},
  props: {
    data: Object,
  },
}
</script>
