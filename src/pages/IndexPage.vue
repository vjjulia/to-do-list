<template>
<div class="main">
  <div class="container-list">To-Do List!</div>
      <q-input class="input" color="teal-9" v-model="list" label="What to do?">
          <template v-slot:prepend>
            <q-icon name="list" />
          </template>
      </q-input>
      <div class="q-pa-md q-gutter-sm">
    <q-btn color="teal-9" v-on:click=(list) style="width: 450px">
      <div class="ellipsis">
        ADD
      </div>
    </q-btn>
  </div>
  {{list}}
</div>
</template>
<script>

export default {
  data() {
    return {
      list: '',
      title: '',
      lists: [],
    };
  },
};
</script>
<style>
.main {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.container-list {
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  padding: 30px;
  color: #079f92;
  font-size: 80px;
}

.input {
  display: flex;
  justify-content: center;
  width: 450px;
}
</style>
