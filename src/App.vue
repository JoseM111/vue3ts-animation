<!-- App.vue -->

// 🌀🌀💻 SCRIPT 💻🌀🌀
<!-- 🎵🎵🔲🔲◾️◾️◾️◾️◾️◾️◾️ -->
<script lang="ts">
import { defineComponent } from 'vue'
import AnimationComponent from "@/components/AnimationComponent.vue"
// ⚫️⚫️☰☰☰☰☰☰☰☰☰☰☰☰☰☰☰☰☰☰☰☰☰☰☰☰☰☰☰☰☰☰☰☰☰☰☰
export default defineComponent({
  name: 'App',
  components: { AnimationComponent },
  //components: {  },
  // Component options data
  data() {
    return {
      flagFade: false,
      flagZoom: true,
      numbers: [11, 15, 17, 14]
    }
  },
  // Component options methods
  methods: {
    addItem() {
      // generates a random number
      const ranNum = Math.floor(
          Math.random() * 100 + 1
      )
    
      const index = Math.floor(
          Math.random() * this.numbers.length
      )
    
      this.numbers.splice(
          index,
          0,
          ranNum
      )
    },
  },
})
</script>
<!-- 🌀🌀💻================================================= -->

// 🌀🌀💻 HTML 💻🌀🌀
<!-- 🎵🎵🔲🔲◾️◾️◾️◾️◾️◾️◾️ -->
<template>
  <!-- 🎵🎵🔲🔲◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️ -->
  <div class="appContainer">
    
    <button
        type="button"
        class="btnFade"
        @click="flagFade = !flagFade"
    >Fade In
    </button>
    
    <button
        type="button"
        class="btnZoom"
        @click="flagZoom = !flagZoom"
    >Zoom In-Out
    </button>
    
    <button
        type="button"
        class="btnList"
        @click="addItem"
    >Add To-List
    </button>
    
    <br>
  
    <!--⚫️ vue-animation ⚫️-->
    <AnimationComponent
        :flag-fade="flagFade"
        :flag-zoom="flagZoom"
        :numbers="numbers"
    />
    
    </div>
  <!-- 🎵🎵🔲🔲◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️ -->
</template>
<!-- 🌀🌀💻================================================ -->

// 🌀🌀💻 STYLES 💻🌀🌀
<!-- 🎵🎵🔲🔲◾️◾️◾️◾️◾️◾️◾️ -->
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss">

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

/// 🎵🔲🔲◾️◾️◾️◾️◾️◾️◾️◾️◾
/** @transition: animation | */

.fade-enter-from {
  opacity: 0;
}

.fade-enter-active {
  transition: all 0.25s linear;
}

.fade-leave-to {
  transition: all 0.25s linear;
  opacity: 0;
}

.zoom-enter-active {
  animation: zoomIn 0.65s linear forwards;
  transition: all 1s linear;
}

.zoom-leave-active {
  animation: zoomOut 0.65s linear forwards;
  transition: all 1s linear;
}

.zoom-enter-from {
  opacity: 0;
}

.zoom-leave-to {
  opacity: 0;
}

.appContainer {
  
  /* 🎵🔲🔲️◾️◾️◾️◾️◾ STYLES INSIDE CONTAINER ◾️◾️◾️◾️◾🔲🔲🎵 */
  li {
    font: bold 53px "Amazon Ember", serif;
    display: block;
    text-align: center;
    cursor: pointer;
    text-shadow: $h1TextShadow;
  }
  
  h1 {
    font-family: "Amazon Ember", serif;
    display: block;
    text-align: center;
    //padding-top: 100px;
    font-size: 53px;
    text-shadow: $h1TextShadow;
    color: #202020;
    letter-spacing: .1em;
  }
  
  .btnFade {
    @include mixinCenterItem;
    
    @include mixinBtnStyled(
        $fontParams: bold 2rem "Amazon Ember Cd RC",
        $bgColor: dodgerblue,
        $txtColor: white,
        $hoverBgColor: darkorange,
        $txtHoverColor: black
    );
  }
  
  .btnZoom {
    @include mixinCenterItem;
    margin-top: 1rem;
    
    @include mixinBtnStyled(
        $fontParams: bold 2rem "Amazon Ember Cd RC",
        $bgColor: violet,
        $txtColor: white,
        $hoverBgColor: red,
        $txtHoverColor: black
    );
  }
  
  .btnList {
    @include mixinCenterItem;
    margin-top: 1rem;
    
    @include mixinBtnStyled(
        $fontParams: bold 2rem "Amazon Ember Cd RC",
        $bgColor: black,
        $txtColor: white,
        $hoverBgColor: dodgerblue,
        $txtHoverColor: red
    );
  }
  
  
}

/// - END OF: appContainer
</style>
<!-- 🌀🌀💻================================================ -->

