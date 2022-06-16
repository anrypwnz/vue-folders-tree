<template>
  <section>
    <div v-if="choose" class="choose">Ваш выбор: {{ choose }}</div>
    <basic-button label="Открыть" @click="toggleShowModal"/>
    <basic-modal :is-open="openModal" :close="toggleShowModal" :apply="onApply" title="Дерево папок">
      <folders-tree :data="data"/>
    </basic-modal>
  </section>
</template>

<script>
import BasicButton from './components/BasicButton.vue'
import BasicModal from "@/components/BasicModal";
import FoldersTree from "@/components/FoldersTree";

export default {
  name: 'App',
  components: {
    FoldersTree,
    BasicButton,
    BasicModal,
  },
  data() {
    return {
      openModal: false,
      isOpen: false,
      data: {
        name: "Testingo",
        children: [
          {name: "orange"},
          {name: "purple"},
          {
            name: "green",
            children: [
              {
                name: "yellow",
                children: [{name: "black"}, {name: "white", children: [{name: 'light'}, {name: 'dark'}]}]
              },
              {name: "red"},
              {name: "blue"},
              {
                name: "brown",
                children: [{name: "pink"}, {name: "grey"}]
              }
            ]
          }
        ]
      },
      selected: '',
      choose: '',
    }
  },
  methods: {
    toggleShowModal() {
      this.openModal = !this.openModal;
    },
    onApply() {
      this.choose = this.selected
      this.toggleShowModal()
    },
  },


}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  margin-top: 60px;
}
.choose {
  margin: 10px;
}
</style>
