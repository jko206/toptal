<template>
  <div class="sample-profiles">
    <h2>Sample Toptal profiles</h2>
    <div class="roles-container">
      <ul class="roles">
        <li
          class="role"
          v-for="(role, idx) in roles"
          :key="idx"
        >
          {{role}}
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
const roles = [
  'Ajax Developer',
  'Android Developer',
  'Angular Developer',
  'API Developer',
  'ASP.NET Developers',
  'Backbone.js Developers',
  'C Developers',
  'C# Developers',
  'C++ Developers',
  'CakePHP',
  'Cocoa Developers',
  'CoffeeScript Developers',
  'DevOps',
  'Drupal Developers',
  'Erlang Developers',
  'Express.js Developers',
  'F# Developers',
  'Front-end Developers',
  'Grails Developers',
  'Hadoop Developers',
  'Hibernate Developers',
  'HTML5 Developers',
  'iOS Developers',
  'Java EE Developers',
  'JavaScript Developers',
  'Machine Learning Developers',
  'MATLAB Developers',
  'MSSQL Developers',
  'MySQL Developers',
  '.NET Developers',
  'Node.js Developers',
  'Objective-C Developers',
  'OpenGL Developers',
  'Perl Developers',
  'PHP Developers',
  'PostgreSQL Developers',
  'PyObjc Developers',
  'PyQT Developers',
  'Python Developers',
  'SalesForce Developers',
  'Scala Developers',
  'Sharepoint Developers',
  'Silverlight Developers',
  'Socket.IO Developers',
  'Spring Developers',
  'SQL Developers',
  'Struts Developers',
  'Sys Admin',
  'Unity or Unity3D Developers',
  'VB.NET Developers',
  'Visual Studio Developers',
  'WordPress Developers',
  'XCode Developers',
]
export default {
  data(){
    return {
      roles,
    }
  }
}
</script>

<style lang="scss" scoped>
@import '../styles/global.scss';
.sample-profiles {
  margin: 50px 0;
  overflow-x: auto;
}
.roles-container {
  column-count: 4;
  max-width: $screen12;
  margin: auto;
  line-height: 1.5;
  width: 1200px;
  ul {
    margin: 0;
    color: $bw-gradient4;
  }
}
</style>
