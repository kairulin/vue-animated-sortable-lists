<template>
<draggable v-model="myArray"  @end="onEnd" tag="transition-group" :component-data="{name:'flip-list'}">
  <template #item="{element}">
    <div>{{element.name}}#{{element.id}}</div>

  </template>
</draggable>
<p><strong>Previous Index:</strong>{{oldIndex}}</p>
<p><strong>New Index:</strong>{{newIndex}}</p>

</template>

<script>
  import draggable from 'vuedraggable'
export default {
  name: "HelloWorld",
  components: {
    draggable,
  },
  data() {
    return {
      myArray: [
        { name: "Student1", id: 0 },
        { name: "Student2", id: 1 },
        { name: "Student3", id: 2 },
        { name: "Student4", id: 3 },
        { name: "Student5", id: 4 },
        { name: "Student6", id: 5 },
      ],
      oldIndex: "",
      newIndex: "",
    };
  },
  methods: {
    onEnd: function (evt) {
      console.log(evt);
      this.oldIndex = evt.oldIndex;
      this.newIndex = evt.newIndex;
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
