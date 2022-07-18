<template>
  <div class="hello">
    <h1>Skillds</h1>
    <draggable
      v-model="myArray"
      v-bind="dragOptions"
      @end="onEnd"
      tag="transition-group"
      :component-data="{ type: 'transition-group', name: 'flip-list' }"
    >
      <template #item="{ element }">
        <div class="sortable">
          <strong>
            {{ element.name }}
          </strong>
          <span>
            {{ element.id }}
          </span>
        </div>
      </template>
    </draggable>
    <p><strong>Previous Index:</strong>{{ oldIndex }}</p>
    <p><strong>New Index:</strong>{{ newIndex }}</p>
  </div>
</template>

<script>
import draggable from "vuedraggable";

export default {
  name: "HelloWorld",
  components: {
    draggable,
  },
  data() {
    return {
      myArray: [
        { name: "1Student", id: 0 },
        { name: "2Student", id: 1 },
        { name: "3Student", id: 2 },
        { name: "4Student", id: 3 },
        { name: "5Student", id: 4 },
        { name: "6Student", id: 5 },
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
  computed: {
    dragOptions() {
      return {
        animation: 200,
        group: "description",
        disabled: false,
        ghostClass: "ghost",
      };
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
h3 {
  margin: 40px 0 0;
}

strong {
  display: inline-block;
}

.sortable {
  width: 100%;
  background: white;
  padding: 1em;
  margin-bottom: 2px;
  cursor: move;

  span {
    float: right;
  }
}

.hello .sortable-drag {
  opacity: 0;
}

// .flip-list-move {
//   transition: transform 0.5s;
// }

.ghost {
  opacity: 0.5;
  background: #c8ebfb;
  border-left:6px solid rgb(0,183,255);
  box-shadow:10px 10px 5px -1px rgba(0,0,0,0.14);

  &::before {
    content: " ";
    position:absolute;
    width:20px;
    height:20px;
    margin-left: -50px;
    background-image:url('../assets/change.svg')
  }
}
</style>
