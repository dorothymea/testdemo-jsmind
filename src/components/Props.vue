<template>
  <div v-if="visible" class="container" :style="{left:x+'px',top:y+'px'}">
    <ul >
      <li v-for="key of Object.keys(props)">
        <span :class="key">{{key}}</span>
        <input type="text" :value="props[key]" :class="key" @blur="editProp"/>
        <span class="action" @click="onDelete" :key="key">x</span>
      </li>
      <li>
        <input placeholder="添加新属性" v-model="newProp"/>
        <span class="action" @click="addProp(newProp)">ok</span>
      </li>
    </ul>
  </div>
</template>

<script>
import { reactive ,ref } from "vue";
export default {
  name: "reactive",
  components: {},
  props:['visible','x','y'],
  setup() {
    const property = reactive({
      prop1:'text1',
      prop2:'text2',
      prop3:'text3'
    })
    let newProp = ''

    function onDelete(e){
      let purpose = e.target.parentElement.firstElementChild.getAttribute('class')
      delete property[purpose]
    }

    function addProp(newPropName){
      if(newPropName) {
        property[newPropName] = '属性'
      }
    }

    function editProp(e){
      let key = e.target.getAttribute('class')
      property[key] = e.target.value
    }
    return { props: property,onDelete,addProp,newProp,editProp};
  },
};
</script>

<style>
ul{
  list-style: none;
  padding: 0;
  margin: 0;
}
li{
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  padding-bottom: 4px;
}
.container{
  padding: 10px;
  z-index: 10;
  position: absolute;
  background: pink;
  width: 250px;
}
</style>