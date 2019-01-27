<template>
  <div class="form-section">
    <h2>Become Toptal leader today</h2>
    <form>
      <div 
        :class="[
          'input-wrapper',
          inputState('name'),
          {'active' : activeInput === 'name'}
        ]"
      >
        <div class="icon-wrap">
          <img src="../assets/icon-name.png" alt="name">
        </div>
        <label for="name">Name</label>
        <input 
          type="text" 
          id="name" 
          v-model="inputs.name"
          @focus="activeInput = 'name'"
          @blur="activeInput = null"
        >
      </div>
      
      <!-- ***** -->

      <div 
        :class="[
          'input-wrapper',
          inputState('email'),
          {'active' : activeInput === 'email'}
        ]"
      >
        <div class="icon-wrap">
          <img src="../assets/icon-email.png" alt="email">
        </div>
        <label for="email">Email</label>
        <input 
          type="email" 
          id="email" 
          v-model="inputs.email"
          @focus="activeInput = 'email'"
          @blur="activeInput = null"
        >
      </div>

      <!-- ***** -->

      <div 
        :class="[
          'input-wrapper',
          inputState('location'),
          {'active' : activeInput === 'location'}
        ]"
      >
        <div class="icon-wrap">
          <img src="../assets/icon-location.png" alt="location">
        </div>
        <label for="location">City &amp; country</label>
        <input 
          type="text" 
          id="location" 
          v-model="inputs.location"
          @focus="activeInput = 'location'"
          @blur="activeInput = null"
        >
      </div>

      <!-- ***** -->
      
      <div 
        :class="[
          'input-wrapper',
          inputState('twitter'),
          {'active' : activeInput === 'twitter'}
        ]"
      >
        <div class="icon-wrap">
          <img src="../assets/icon-twitter.png" alt="twitter">
        </div>
        <label for="twitter">Twitter</label>
        <input 
          type="text" 
          id="twitter" 
          v-model="inputs.twitter"
          @focus="activeInput = 'twitter'"
          @blur="activeInput = null"
        >
      </div>

      <!-- ***** -->
      
      <div 
        :class="[
          'input-wrapper',
          'comment-wrapper',
          inputState('comment'),
          {'active' : activeInput === 'comment'}
        ]"
      >
        <div class="icon-wrap">
          <img src="../assets/icon-comment.png" alt="comment">
        </div>
        <label for="comment">Comment</label>
        <textarea 
          id="comment" 
          v-model="inputs.comment" 
          @focus="activeInput = 'comment'"
          @blur="activeInput = null"
        ></textarea>
      </div>

      <!-- ***** -->
      
      <div class="input-wrapper submit-wrapper">
        <input type="submit" value="Submit">
      </div>
    </form>
  </div>
</template>
<script>
function inputValidator(field, input){
  let validators = {
    name(input) {
      // return true if input has no number in it
      return !/\d+/.test(input)
    },
    email(input) {
      // got the regex from: https://emailregex.com/
      return /^[A-Z0-9._%+-]+@[A-Z0-9.-]+\.[A-Z]{2,63}$/i.test(input)
    },
    location(input) {
      // as long as it doesn't contain numbers, it's true
      return this.name(input) 
    },
    twitter(input) {
      return /^@?(\w){1,15}$/.test(input)
    },
    comment(){
      return true
    }
  }
  return validators[field](input)
}

export default {
  data(){
    return {
      activeInput: null,
      inputs: {
        name: '',
        email: '',
        location: '',
        twitter: '',
        comment: '',
      }
    }
  },
  methods: {
    inputState(field) {
      let currVal = this.inputs[field]
      if(currVal === '') return
      else {
        return inputValidator(field, currVal) ? 'valid' : 'invalid'
      }
    }
  }
}

</script>
<style lang="scss" scoped>
@import '../styles/global.scss';
h2 {
  margin: 50px auto;
}
form {
  max-width: $screen9;
  margin: auto;
  display: grid;
  grid-row-gap: 20px;
  grid-column-gap: 10px;
  grid-template-rows: 4rem;
  grid-auto-rows: 4rem;
  padding: 10px;
  .input-wrapper {
    width: 100%;
    height: calc(100% + 2px);
    overflow: hidden;
    &:not(.submit-wrapper){
      border: 1px solid $bw-gradient3;
      border-radius: 5px;
      background: $bw-gradient6;
      color: $bw-gradient4;
    }
    .icon-wrap {
      display: block;
      width: 1rem;
      height: 1rem;
      position: absolute;
      top: 1.5rem;
      left: 0.5rem;
      z-index: 20;
      img {
        opacity: 0.6;
        width: 100%;
      }
    }
    label {
      display: block;
      height: 1rem;
      position: absolute;
      top: 1.5rem;
      left: 2rem;
      z-index: 20;
      transition: top 0.05s ease-in-out;
    }
    input:not([type="submit"]), textarea {
      position: absolute;
      top: 0;
      padding: 1.5rem 2rem;
      border: 0;
      outline: none;
      height: 100%;
      font-size: 1rem;
      /*
        -1px: same reason as below
        2px: to account for border of the wrapper.
            w/o it, the auto-complete dropdown looks weird
      */
      left: -1px;
      width: calc(100% + 2px);
      box-sizing: border-box;
      resize: none;
    }
    &.comment-wrapper {
      grid-row: span 4;
    }
    &.submit-wrapper {
      @extend %dead-center;
      input {
        @extend %dead-center;
        background: #61c891;
        cursor: pointer;
        border-radius: 5px;
        border: 1px solid #3a7d57;
        color: white;
        text-transform: uppercase;
        height: 50px;
        width: 220px;
        appearance: none;
        -webkit-appearance: none;
      }
    }

    &.active, &.valid, &.invalid {
      label {
        top: 0.5rem;
        font-size: 0.75rem;
      }
    }
    &.invalid {border-color: red;}
  }
  @media(min-width: $screen6) {
    grid-template-columns: 1fr 1fr;
    .input-wrapper{
      &.comment-wrapper {
        grid-row: span 2;
        grid-column: span 2;
      }
      &.submit-wrapper {
        grid-column: span 2;
      }
    }
  }
}
</style>
