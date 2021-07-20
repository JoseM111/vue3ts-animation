<!-- AnimationComponent.vue -->

// 🌀🌀💻 SCRIPT 💻🌀🌀
<!-- 🎵🎵🔲🔲◾️◾️◾️◾️◾️◾️◾️ -->
<script lang="ts">
import { defineComponent, PropType } from 'vue'
// ⚫️⚫️☰☰☰☰☰☰☰☰☰☰☰☰☰☰☰☰☰☰☰☰☰☰☰☰☰☰☰☰☰☰☰☰☰☰☰
export default defineComponent({
  name: 'AnimationComponent',
  // Component options props
  props: {
    flagFade: {
      type: Boolean as PropType<FlagType['flagFade']>,
      required: true
    },
    flagZoom: {
      type: Boolean as PropType<FlagType['flagZoom']>,
      required: true
    },
    numbers: {
      type: Array as PropType<Array<FlagType['numbers']>>,
      required: true
    },
  },
  // Component options methods
  methods: {
    removeItem(index: number) {
      this.numbers.splice(index, 1)
    }
  }
})
</script>
<!-- 🌀🌀💻================================================= -->

// 🌀🌀💻 HTML 💻🌀🌀
<!-- 🎵🎵🔲🔲◾️◾️◾️◾️◾️◾️◾️ -->
<template>
  <!-- 🎵🎵🔲🔲◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️ -->
  <div class="animationContainer">
    
    <transition name="fade" mode="out-in">
      <h1 v-if="flagFade" key="main">
        <b>@Vue3-fade-animation</b>
      </h1>
      <h1 v-else key="secondary">
        <b>default: @Vue3-UP</b>
      </h1>
    </transition>
    
    <transition name="zoom" type="animation" appear>
      <h1 v-if="flagZoom">
        <b>@Vue3-zoom-animation</b>
      </h1>
    </transition>
    
    <ul>
    <li v-for="(num, index) in numbers"
        key="num"
        @click="removeItem(index)"
    >
      Number: {{ num }}
    </li>
  </ul>
  
  </div>
  <!-- 🎵🎵🔲🔲◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️ -->
</template>
<!-- 🌀🌀💻================================================ -->

// 🌀🌀💻 STYLES 💻🌀🌀
<!-- 🎵🎵🔲🔲◾️◾️◾️◾️◾️◾️◾️ -->
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss">
.animationContainer {
  
  /*🎵🔲🔲️◾️◾️◾️◾️◾ STYLES INSIDE CONTAINER ◾️◾️◾️◾️◾🔲🔲🎵 */
  $h1TextShadow: 2px 2px 1px rgba(0, 0, 0, 0.4);
  
  /** @mixins: mixinBtnStyled | */
  
  @mixin mixinBtnStyled($fontParams, $bgColor, $txtColor, $hoverBgColor, $txtHoverColor) {
    padding: 20px 40px;
    font: $fontParams;
    background: $bgColor;
    color: $txtColor;
    border-radius: 1.5rem;
    cursor: pointer;
    outline: none;
    border: none;
    box-shadow: 0 10px 6px -6px #777;
    
    &:hover {
      transition: all 0.3s ease-in;
      background: $hoverBgColor;
      color: $txtHoverColor;
      opacity: 0.90;
    }
    
    &:active {
      opacity: 0.15;
      transition: all 0.3s ease-in;
    }
  }
  
  @mixin mixinCenterItem() {
    margin: 10rem auto 0;
    display: block;
  }
  
  /** @keyframes | */
  
  @keyframes zoomIn {
    from {
      transform: scale(0, 0);
    }
    to {
      transform: scale(1, 1);
    }
  }
  
  @keyframes zoomOut {
    from {
      transform: scale(1, 1);
    }
    to {
      transform: scale(0, 0);
    }
  }
}

/// - END OF: animationContainer
</style>
<!-- 🌀🌀💻================================================ -->

