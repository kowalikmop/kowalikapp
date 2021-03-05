<template>
  <div class="container">
          <div class="input-group mb-3">
            <input v-model="newtitle" type="text" class="form-control" placeholder="Dodaj zadanie">
            <div class="input-group-append">
              <button @click="addTask" class="btn btn-success" type="submit">Dodaj</button>
            </div>
          </div>
  <div v-for="item in elements" :key="item.id"
  v-bind:class="{complited: item.statuscomplite}" class="alert alert-success">
    <button v-if="!item.statuscomplite" @click="done(item.id)" type="button" class="close">
      &times;</button>
    {{item.title}}</div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      idek: 0,
      newtitle: '',
      elements: [],
    };
  },
  methods: {
    addTask() {
      if (this.newtitle) {
        this.elements.push({ title: this.newtitle, statuscomplite: false, id: this.idek += 1 });
        this.newtitle = '';
      }
    },
    done(id) {
      const index = this.elements.findIndex((el) => el.id === id);
      this.elements[index].statuscomplite = true;
    },
  },
};
</script>
<style scoped>
input {
              width: 200px;
        }
.fade-enter-active, .fade-leave-active {
  transition: all .3s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
font-size: 40px;
}
  .complited {
          opacity: 0.5;
  }
</style>
