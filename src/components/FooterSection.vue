<template>
  <div class="footer-section">
    <div class="footer-container">
      <div class="top">
        <span>
          Need immediate assistance?&nbsp;
        </span> 
        <span class="bold">
          Call us:
          <a href="tel:+18886043188">888.604.3188</a>
        </span>
      </div>
    
      <div class="bottom">
        <span>&copy; Copyright 2010-2014</span>
        <span class="divider">&nbsp;|&nbsp;</span>
        <span>Toptal, LLC</span>
        <span class="divider">&nbsp;|&nbsp;</span>
        <span>
          <a href="#">Privacy Policy</a>
          |
          <a href="#">Terms of Service</a>
        </span>
      </div>
    </div>
  </div>
</template>
<style lang="scss" scoped>
@import '../styles/global.scss';
.footer-section {
  background: #3b67a7;
  padding: 20px;
  min-height: 200px;
  display: flex;
  align-items: center;
}
.footer-container {
  display: flex;
  max-width: $screen12;
  flex-direction: column;
  align-items: center;
  color: white;
  line-height: 1.5;
  width: 100%;
  height: 100%;
  
  a {
    color: white;
    &:hover {
      text-decoration: underline;
    }
  }

  .top, .bottom {
    display: flex;
    flex-direction: column;
    width: 300px;
    text-align: center;
    margin: 20px auto;
  }
  .divider {
    display: none;
  }
  @media (min-width: $screen6) {
    flex-direction: row-reverse;
    justify-content: space-between;
    align-items: flex-start;
    margin: auto;
    
    .top, .bottom {
      margin: 0;
    }
    .top {
      text-align: right;
    }
    .bottom {
      text-align: left;
    }
  }
  @media (min-width: $screen12) {
    
    .divider {
      display: inline;
    }
    .top, .bottom {
      flex-direction: row;
      width: initial;
    }
  }
}

</style>
