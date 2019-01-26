<template>
  <div class="leader-section">
    <h2>Meet the Toptal Leader Team</h2>
    <div class="section-main">
      <div 
        class="profile-container"
        v-for="profile in profiles"
        :key="profile.name.replace(/\s/g, '-')"
      >
        <div class="profile-pic-container">
          <img :src="profile.picSrc" :alt="profile.name" />
        </div>
        <div class="profile-text">
          <span class="profile-name">
            {{profile.name}}
          </span>
          <span class="profile-location">
            {{profile.location}}
          </span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      profiles: [
        {
          name: 'Luboš Volkov',
          picSrc: require('../assets/profile-photo.png'),
          location: 'New Zealand'
        },
        {
          name: 'Michael Vasko',
          picSrc: require('../assets/profile-photo.png'),
          location: 'Slovakia'
        },
        {
          name: 'Yummygum',
          picSrc: require('../assets/profile-photo.png'),
          location: 'Sweden'
        },
        {
          name: 'Nicholas Will',
          picSrc: require('../assets/profile-photo.png'),
          location: 'USA'
        },
        {
          name: 'Hanna Aase',
          picSrc: require('../assets/profile-photo.png'),
          location: 'Russia'
        },
      ]
    }
  }
}
</script>

<style lang="scss" scoped>
@import '../styles/global.scss';
.section-main {
  display: grid;
  grid-template-columns: 1fr;
  margin: 50px auto;
  max-width: $screen12;
}
.profile-container {
  width: 180px;
  margin: auto;
  flex: 0 0 auto;
}
.profile-pic-container {
  background: green;
  border-radius: 5px;
  overflow: hidden;
  width: 180px;
  height: 180px;
  @extend %dead-center;
  img {
    filter: grayscale(1);
    height: 100%;
  }
}
.profile-text {
  padding: 10px;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.profile-name {
  font-size: 1.125rem;
  color: $blue0;
}
.profile-location {
  font-size: 0.875rem;
  color: $bw-gradient3;
}


@media(min-width: $screen45) {
  .section-main {
    grid-template-columns: 1fr 1fr;
    grid-row-gap: 20px;
  }
  .profile-container {
    &:nth-child(5) {
      grid-column: span 2;
    }
  }
}
@media(min-width: $screen6) {
  .section-main {
    grid-template-columns: repeat(6, 1fr);
    grid-row-gap: 20px;
  }
  .profile-container {
    grid-column: span 2;
    &:nth-child(4), &:nth-child(5) {
      grid-column: span 3;
    }
  }
}
@media(min-width: $screen9) {
  .section-main {
    grid-template-columns: repeat(5, 1fr);
    grid-row-gap: 20px;
  }
  .profile-container {
    grid-column: span 1;
    &:nth-child(4), &:nth-child(5) {
      grid-column: span 1;
    }
  }
}
</style>
