<template>
  <div class="header-section">
    <div class="blue-streak"></div>
    <div 
      :class="[
        'menu-toggle',
        {'active' : isSideBarActive}
      ]"
      @click="isSideBarActive = !isSideBarActive"    
    >
      <button class="join-toptal-text base-button">
        JOIN TOPTAL
      </button>
      <div class="tribar">
        <div class="bar"></div>
        <div class="bar"></div>
        <div class="bar"></div>
      </div>
    </div>
    <div class="top">
      <div class="left">
        <img src="../assets/logo.png" alt="Toptal logo">
      </div>
      <div class="right">
        <a href="#" class="sign-in">
          Sign in
        </a>
        <span class="join-toptal-text">
          JOIN TOPTAL
        </span>
        <button class="base-button">
          Company
        </button>
        <button class="base-button">
          Developer
        </button>
      </div>
    </div>
    <div class="gray-streak"></div>
    <div class="bottom">
      <div class="left">
        <component
          v-for="idx in menuItems.length * 2 - 1"
          :key="idx"
          :is="idx%2 === 1 ? 'a' : 'span'"
          :href="idx%2 === 1 && '#'"
        >
          {{idx%2 === 1 ? menuItems[Math.floor(idx/2)] : ' | '}}
        </component>
        <a href="#">
          Sign In
        </a>
      </div>
      <div class="right">
        CALL US: 
        <a>
          888.604.8188
        </a>
      </div>
    </div>
    <div
      :class="[
        'side-bar-container',
        {'active' : isSideBarActive}
      ]"
    >
      <div class="side-bar">
        <div class="side-bar-menu">
          <a href="#" v-for="(item, idx) in menuItems" :key="idx">
            {{item}}
          </a>
        </div>
        <div class="side-bar-buttons">
          <div>JOIN TOPTAL</div>
          <button class="base-button">
            Company
          </button>
          <button class="base-button">
            Developer
          </button>
        </div>
        <div class="side-bar-phone-number">
          CALL US: 
          <a class="phone-number" href="tel:+18886048188">
            888.604.8188
          </a>
        </div>
      </div>
    </div>
  </div>
</template>
<style lang="scss" scoped>
@import '../styles/global.scss';
.blue-streak {
  background: linear-gradient(to right, #5e89c6 0%, #5e89c6 20%, #3863a0 20%, #3863a0 40%, #5e89c6 40%, #5e89c6 60%, #3863a0 64%, #3863a0 80%, #5e89c6 80%, #5e89c6 100%);
  height: 2px;
}
.header-section {
  width: 100%;
  background: #fcfcfc;
  min-height: 80px;
  color: $bw-gradient4;
  z-index: 10;
  font-size: 0.875rem;
  // overflow: hidden;
  
}
.top {
  height: 80px;
  .left {
    @extend %dead-center;
    height: 100%;
  }
  .right {
    display: none;
    a {
      color: $bw-gradient4;
      text-transform: uppercase;
      text-decoration: none;
    }
    span {
      color: $bw-gradient2;
    }
  }
}
.bottom {
  .left, .right {
    display: none;
  }
  .right {
    a {
      text-decoration: underline;
    }
  }
}
.gray-streak {
  height: 1px;
  background: #e5e5e5;
}
.menu-toggle{
  .join-toptal-text {
    display: none;
  }
  .tribar {
    position: absolute;
    width: 50px;
    height: 50px;
    right: 10px;
    padding: 16px 10px;
    top: 15px;
    z-index: 10;
    display: flex;
    flex-direction: column;
    cursor: pointer;
    justify-content: space-between;
    .bar {
      width: 100%;
      height: 3px;
      background: gray;
    }
  }
}

.side-bar-container {
  width: 0;
  overflow-x: hidden;
  position: absolute;
  top: 82px;
  right: 0;
  height: calc(100vh - 82px);
  background: white;
  transition: width 0.2s ease-in-out;
  &.active {
    width: 100vw;
  }
}

.side-bar{
  width: 100%;
  background: white;
  // position: absolute;
  // top: 82px;
  // height: calc(100vh - 82px);
  // right: -100%;
  transition: right 0.2s ease-in-out;
  border-left: 1px solid gainsboro;
  &.active {
    right: 0;
  }
}
  .side-bar-menu {
    display: flex;
    flex-direction: column;
    max-height: calc(100% - 80px);
    justify-content: flex-start;
    a {
      height: 40px;
      font-size: 1.25rem;
      border-bottom: 1px solid gainsboro;
      display: flex;
      align-items: center;
      padding: 20px;
    }
  }

  .side-bar-buttons {
    display: flex;
    flex-wrap: wrap;
    div {
      text-align: center;
      padding: 10px;
      width: 100%;
      flex: 0 0 auto;
      flex-wrap: wrap;
    }
    button {
      margin: 10px auto;
    }
  }

  .side-bar-phone-number {
    bottom: 0;
    height: 80px;
    width: 100%;
    background: white;
    @extend %dead-center;
    border-top: 1px solid gainsboro;
    a {
      text-decoration: underline;
    }
  }

@media (min-width: $screen45){
  .side-bar-container {
    width: 0;
    &.active {
      width: 300px;
    }
  }
}
@media (min-width: $screen6){
  .top {
    padding: 0 10px;
  }
  .bottom {
    padding: 0 10px;
    .left {
      display: flex;
      height: 40px;
      background: #ffffff05;
      align-items: center;
      a {
        margin: 5px;
        text-transform: uppercase;
        color: $bw-gradient4;
      }
    }
  }
  .menu-toggle {
    z-index: 20;
    .join-toptal-text {
      display: block;
      position: absolute;
      right: 15px;
      top: 15px;
    }
    .tribar {
      display: none;
    }
  }
  .side-bar-container {
    background: initial;
    &.active {
      width: initial;
      height: initial;
      overflow: visible;
      .side-bar {
        display: block;
      }
    }
  }
  .side-bar {
    right: 15px;
    width: 250px;
    padding: 5px;
    border-radius: 5px;
    height: inherit;
    background: white;
    border: 1px solid $bw-gradient3;
    box-shadow: 1px 1px 1px gray;
    display: none;
    
    .side-bar-menu {
      display: none;
    }
    
    .side-bar-buttons {
      display: block;
      div {
        display: none;   
      }
    }
    .side-bar-phone-number {
      position: relative;
      padding: 10px;
      height: inherit;
    }
    &.active {
      display: block;
      right: 10px;
    }
  }
}
@media(min-width: $screen9){
  .side-bar, .menu-toggle{
    display: none;
    &.active {
      display: none;
    }
  }
  .top, .bottom {
    display: flex;
    justify-content: space-between;
    padding: 0 10px;
    max-width: $screen12;
    margin: auto;
    .right {
      display: flex;
      align-items: center;
      justify-content: space-between;
      span {
        width: 100px;
        margin: 10px;
      }
    }
  }
  .top .right{
    width: 470px;
  }
}
</style>

<script>
export default {
  data(){
    return {
      menuItems: [
        'Why',
        'How',
        'What',
        'Contact',
        'Team',
        'Blog',
      ],
      isSideBarActive: false
    }
  },
  mounted() {
    window.addEventListener('scroll', e=> {
      if(window.pageYOffset > 80) this.isSideBarActive = false
    })
  }
}
</script>
