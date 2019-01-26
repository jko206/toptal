<template>
  <div class="why-section">
    <h2>Why become a Toptal Leader?</h2>
    <div class="section-main">
      <div 
        class="sub-section"
        v-for="(item, idx) in contentItems"
        :key="idx"
      >
        <div class="image-container">
          <img :src="item.image.src" :alt="item.image.alt">
        </div>
        <div class="divider"></div>
        <div class="text">
          {{item.text}}
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data(){
    return {
      contentItems: [
        {
          image: {
            src: require('../assets/spaceman1.png'),
            alt: 'Spaceman 1'
          },
          text: `
            Lead your community by hosting exclusive events, 
            doing targeted outreach and engaging with your 
            network while leveraging Toptal's growing 
            international brand.
          `,
        },
        {
          image: {
            src: require('../assets/spaceman2.png'),
            alt: 'Spaceman 2'
          },
          text: `
            Help build our community of extraordinary talent as
            a Toptal ambassador in your city. Be the foundation
            for growth and launch your profile's presence.
          `,
        },
        {
          image: {
            src: require('../assets/spaceman3.png'),
            alt: 'Spaceman 3'
          },
          text: `
            Become a prominent thought leader in your local engineering
            community. Be recognized for networking the brightest and 
            most innovative minds together.Work with an incredible team 
            from across the globe. Receive more opportunities to work
            on client projects. Earn commissions as your Toptal
            community grows.
          `,
        },
      ]
    }
  }
}
</script>

<style lang="scss" scoped>
@import '../styles/global.scss';
.section-main {
  margin: auto;
  max-width: 400px;
  padding: 10px;
  color: $bw-gradient3;
  line-height: 1.5;
  text-align: justify;
}
.sub-section {
  margin: 50px auto;
}
.image-container {
  height: 200px;
  text-align: center;
  margin-bottom: 50px;
  img {
    height: 100%;
  }
}

.divider {
  width: 220px;
  height: 4px;
  margin: 20px auto;
  background: $bw-gradient5;
}
.text {
  max-width: 280px;
  margin: auto;
}
@media(min-width: $screen9){
  .section-main {
    display: grid;
    grid-gap: 20px;
    grid-template-columns: repeat(3, 1fr);
    max-width: $screen12;
  }
}
</style>
