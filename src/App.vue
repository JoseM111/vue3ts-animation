<!-- App.vue -->

// 🌀🌀💻 SCRIPT 💻🌀🌀
<!-- 🎵🎵🔲🔲◾️◾️◾️◾️◾️◾️◾️ -->
<script lang="ts">
import { defineComponent } from 'vue'
// ⚫️⚫️☰☰☰☰☰☰☰☰☰☰☰☰☰☰☰☰☰☰☰☰☰☰☰☰☰☰☰☰☰☰☰☰☰☰☰
export default defineComponent({
  name: 'App',
  //components: {  },
  // Component options data
  data() {
    return { flag: false }
  },
})
</script>
<!-- 🌀🌀💻================================================= -->

// 🌀🌀💻 HTML 💻🌀🌀
<!-- 🎵🎵🔲🔲◾️◾️◾️◾️◾️◾️◾️ -->
<template>
  <!-- 🎵🎵🔲🔲◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️ -->
  <div class="appContainer">
    
    <button type="button" @click="flag = !flag">
      Toggle
    </button>
    
    <br>
    
    <transition name="fade">
      <h1 v-if="flag">
        <b>@Vue3-Animation</b>
      </h1>
    </transition>
    
    
  </div>
  <!-- 🎵🎵🔲🔲◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️◾️ -->
</template>
<!-- 🌀🌀💻================================================ -->

// 🌀🌀💻 STYLES 💻🌀🌀
<!-- 🎵🎵🔲🔲◾️◾️◾️◾️◾️◾️◾️ -->
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss">

$h1TextShadow: 2px 2px 1px rgba(0,0,0,0.4);

/** @mixins: mixinBtnStyled | */

@mixin mixinBtnStyled($fontParams, $bgColor, $txtColor, $hoverBgColor, $hoverColor) {
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
    color: $hoverColor;
    opacity: 0.90;
  }
  
  &:active {
    opacity: 0.15;
    transition: all 0.3s ease-in;
  }
}

/** @transition: animation | */
.fade-enter-from {
  opacity: 0;
}
.fade-enter-active {
  transition: all 0.25s linear;
}

@mixin mixinCenterItem() {
  margin: 10rem auto 0;
  display: block;
}

/// 🎵🔲🔲◾️◾️◾️◾️◾️◾️◾️◾️◾

.appContainer {
  
  /* 🎵🔲🔲️◾️◾️◾️◾️◾ STYLES INSIDE CONTAINER ◾️◾️◾️◾️◾🔲🔲🎵 */
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
  
  button {
    @include mixinCenterItem;
    
    @include mixinBtnStyled(
        $fontParams: bold 2rem "Amazon Ember Cd RC",
        $bgColor: dodgerblue,
        $txtColor: white,
        $hoverBgColor: darkorange,
        $hoverColor: black
    );
  }
}

/// - END OF: appContainer
</style>
<!-- 🌀🌀💻================================================ -->

