<template>
  <div id="app">
    <HeaderSection/>
    <MainSection/>
    <WhySection/>
    <LeaderSection/>
    <CollageSection/>
    <FormSection/>
    <SampleProfiles/>
    <FooterSection/>
  </div>
</template>

<script>
import HeaderSection from './components/HeaderSection.vue'
import MainSection from './components/MainSection.vue'
import WhySection from './components/WhySection.vue'
import LeaderSection from './components/LeaderSection.vue'
import CollageSection from './components/CollageSection.vue'
import FormSection from './components/FormSection.vue'
import SampleProfiles from './components/SampleProfiles.vue'
import FooterSection from './components/FooterSection.vue'


export default {
  name: 'app',
  components: {
    HeaderSection,
    MainSection,
    WhySection,
    LeaderSection,
    CollageSection,
    FormSection,
    SampleProfiles,
    FooterSection,
  }
}
</script>
<style lang="scss">
// @import './styles/global.scss';

:root{
  font-size: 16px;
  color: #030303;
  font-family:'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif
}
body{
  margin: 0;
  padding: 0;
}
div, span {
  position: relative;
  box-sizing: border-box;
}
a {
  text-decoration: none;;
  color: #030303;
}

h2 {
  font-size: 1.25rem;
  text-decoration: underline;
  margin: 50px auto;
  color: #484848;
  text-align: center;
}
</style>
