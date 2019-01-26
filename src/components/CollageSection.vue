<template>
  <div class="collage-section">
    <h2>Want to be a part of this <span>growing community?</span></h2>
    <div class="collage">
      <div class="piece"></div>
      <div class="piece"></div>
      <div class="piece"></div>
      <div class="piece"></div>
      <div class="piece"></div>
      <!-- -->
      <div class="piece"></div>
      <div class="piece"></div>
      <div class="piece"></div>
      <div class="piece"></div>
      <div class="piece"></div>
      <!-- -->
      <div class="piece"></div>
      <div class="piece"></div>
      <div class="piece"></div>
      <div class="piece"></div>
      <div class="piece"></div>
      <!-- -->
      <div class="piece"></div>
      <div class="piece"></div>
      <div class="piece"></div>
      <div class="piece"></div>
      <div class="piece"></div>
      <!-- -->
    </div>
  </div>
</template>
<style lang="scss" scoped>
@import '../styles/global.scss';
.collage-section {
  @extend %dead-center;
  height: 100vh;
  margin: 100px 0;
  h2 {
    text-decoration: none;
    z-index: 20;
    font-size: 3rem;
    font-weight: 100;
    line-height: 2;
    color: white;
    text-shadow: 3px 3px 5px black;
    span {
      font-weight: bold;
    }
  }
}
.collage {
  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-gap: 5px;
  position: absolute;
  overflow: hidden;
  width: 100%;
  height: 100%;
  
  .piece {
    filter: grayscale(1) brightness(0.7);
    border-radius: 5px;
    background: gray;
    width: 100%;
    padding-bottom: 100%;
    background: url('../assets/collaborating_employees.jpg');
    background-size: cover;
    background-repeat: no-repeat;
    &:nth-child(1) {
      grid-column: span 2;
      grid-row: span 2;
    }
    &:nth-child(2) {
      background-size: auto 200%;
      background-position: -227px -100px;
    }
    &:nth-child(3) {
      background-size: auto 200%;
      background-position: right -100px;
    }
    &:nth-child(4){
      grid-column: span 2;
      background-position: 0 -100px;
    }
  }
}
@media(min-width: $screen6) {
  .collage-section {
    max-height: 500px;
  }
  .collage {
    grid-template-rows: 220px 280px;
    grid-template-columns: repeat(3, 250px);
    grid-auto-columns: 250px;
    grid-auto-flow: column dense;
    .piece {
      width: 100%;
      height: 100%;
      padding: 0;
      background-size: 900px 600px;

      &:nth-child(7n + 1) {
        grid-column: span 2;
        grid-row: span 2;
      }
      &:nth-child(7n + 2){
        grid-column: span 1;
        background-position: -180px -90px;
        background-size: auto 200%;
      }
      &:nth-child(7n + 3) {
        grid-column: span 2;
      }
      &:nth-child(7n + 4) {
        grid-column: span 1;
        background-position: right -90px;
        background-size: auto 200%;
      }
      &:nth-child(7n + 5) {
        grid-column: span 3;
        grid-row: span 2;
      }
      &:nth-child(7n + 6), &:nth-child(7n + 7) {
        grid-column: span 1;
        grid-row: span 1;
      }
    }
  }
}
</style>
