<template>
  <div class="page">
    <input v-model="value" />
    <button @click="add">添加</button>
    <transition>
      <transition-group name="fade">
        <div class="item" v-for="(item, index) in list" :key="index">
          <div class="text">{{ item }}</div>
          <button class="btn" @click="() => deleteItem(index)">delete</button>
        </div>
      </transition-group>
    </transition>
  </div>
</template>

<script type="text/ecmascript-6">
export default {
  data() {
    return {
      list: [],
      value:''
    }
  },
  methods: {
    add() {
      this.list.push(this.value)
    },
	deleteItem(key) {
		this.list = this.list.filter((item, index) =>index !== key)
	}
  }
}
</script>

<style scoped lang="scss">
.item {
  width: 400px;
  margin: 0 auto;
  margin-top: 20px;
  // display: flex;
  border: 1px solid red;
}
.text {
  display: inline-block;
}
.btn {
  float: right;
  border: 1px solid blue;
}
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}
</style>
