<template>
  <div class="main">
    <div class="container-list">To-Do List!</div>
      <q-input class="input" color="teal-9" v-model="input" label="What to do?">
        <template v-slot:prepend>
          <q-icon name="list" />
        </template>
      </q-input>
      <div class="q-pa-md q-gutter-sm">
      <q-btn class="button-input" v-on:click="add()" style="width: 450px">
        <div class="ellipsis">ADD</div>
      </q-btn>
      </div>
    <div class="msg">{{msg}}</div>
    <q-card class="list" color="" flat bordered v-for="(item, index) in lists" :key="index">
      <div class="title">
        <div class="position">
          <q-radio v-model="item.shape" v-on:click="marca(index)"/>
        </div>
        {{item.value}}
      </div>
      <div class="remove" v-on:click="remove(index)">
        <q-icon name="delete"/>
      </div>
    </q-card>
  </div>
  </template>

<script>

export default {
  data() {
    return {
      msg: '',
      input: '',
      lists: [],
      shape: '',
    };
  },

  methods: {
    add() {
      if (this.input === '') {
        this.msg = 'A tarefa não pode ser vazia';
      } else {
        this.lists.push({
          shape: false,
          value: this.input,
        });
        this.input = '';
        this.msg = '';
      }
    },
    remove(index) {
      this.lists.splice(index, 1);
    },
    marca(index) {
      if (this.lists[index].checked) {
        this.lists[index].checked = true;
      } else {
        this.lists[index].checked = false;
      }
    },
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

  .list {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 10px;
    height: 100px;
    width: 450px;
    margin: 5px;
  }

  .title {
    display: flex;
    align-items: center;
  }

  .position {
    margin-right: 10px;
  }

  .icon {
    background-color: #079f92;
    color: white;
  }

  .remove {
    font-size: 26px;
    color: #079f92;
    cursor: pointer;
  }

  .button-input {
    background-color: #079f92;
    color: white;
  }

  .msg {
    color: red;
    font-weight: 600;
  }

</style>
