<script>
export default {
  data() {
    return {
      hoveredIndex: null,
      links: [
        { name: 'Home', actions: ['Action 1', 'Another action 1', 'Something else here 1'] },
        { name: 'Courses', actions: ['A ction2', 'Another action 2', 'Something else here2']  },
        { name: 'About Us', actions: ['Ac tion3', 'Another action 3', 'Something else here3']  },
        { name: 'News', actions: ['Act ion4', 'Another action 4', 'Something else here4']  },
        { name: 'Pages', actions: ['Acti on5', 'Another action 5', 'Something5 else here5 '] },
        { name: 'Contact', actions: ['Actio n6', 'Another action 6', 'Something else here6 '] },
        { name: 'Purchase', actions: ['Action 7', 'Another action 7', 'Something else here 7'] },
      ]
    }
  },
  methods: {
    hovered(index) {
      this.hoveredIndex = index;
    },
    unHovered() {
      this.hoveredIndex = null;
    }
  }
}
</script>


<template>
  <header>
    <div v-for="(element, index) in links" :key="index" class="element">
      <p @mouseover="hovered(index)" @mouseleave="unHovered">{{ element.name }} </p>
      <div class="dropdown" :class="{ active: hoveredIndex === index }" v-if="element.actions">
        <p v-for="contenuto in element.actions" :key="contenuto">{{ contenuto }}</p>
      </div>
    </div>
  </header>
</template>

<style scoped>
header {
  border: 2px dashed green;
  width: 100%;
  margin-top: 5rem;
  display: flex;
  padding: 1rem;
  justify-content: center;
}

.element {

  position: relative;
}

.dropdown {
  position: absolute;
  padding: 1rem;
  min-width: 10px;
  top: 160px;
  transition: 0.4s ease;
  background: transparent;
  color: transparent;
  border: 2px dashed transparent;
  text-wrap: nowrap;
}

.active {
  top: 90px;
  border: 2px dashed purple;
  background: rgba(128, 0, 128, 0.336);
  color: black;
}

.dropdown p {
  padding: 0.5rem 0;
}

p {
  padding: 3rem;

}

.element:hover {
  cursor: pointer;
}
</style>
