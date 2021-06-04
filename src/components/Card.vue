<template>
  <div
    :class="`column is-${colsCount}`"
    style="perspective: 1000px"
    @click="$emit('click-me', { id: card.id, uid: card.uid })"
  >
    <div class="flipcard">
      <!-- <img :src="`./assets/${card.name}.svg`" /> -->
      <div class="front-face">
        <span>{{ card.name }}</span>
      </div>
      <div class="back-face"></div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Card",
  props: {
    card: Object,
    cols: Number,
  },
  computed: {
    colsCount: function () {
      const map = {
        4: "3",
        6: "2",
      };
      return map[this.cols];
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.flipcard {
  position: relative;
  width: 120px;
  height: 120px;
  transform-style: preserve-3d;
  transition: transform 0.5s;
}


.front-face,
.back-face {
  position: absolute;
  width: 100%;
  height: 100%;
  backface-visibility: hidden;
  background-color: purple;
}

.front-face {
  display: flex;
  align-items: center;
  justify-content: center;
  color:white;
  font-size: 60px;
}

.front-face {
  transform: rotateY(180deg);
}

/* span {
  font-size: 60px;
  color: white;
} */


.visible .flipcard {
  transform: rotateY(180deg);
}

.done {
  animation: fadeOut 0.5s linear 0.5s forwards;
}

@keyframes fadeOut {
  0% {
    opacity: 1;
  }
  100% {
    opacity: 0;
  }
}
</style>
