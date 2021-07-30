<template>
<div class="container">
  <div class='tag-input'>
    <div v-for='(tag, index) in tags' :key='tag' class='tag-input__tag'>
      {{ tag }}
      <span @click='removeTag(index)'>x</span>
    </div>
    <input
      type='text'
      placeholder="Enter a Tag"
      class='tag-input__text'
      @keydown.enter='addTag'
      @keydown.188='addTag'
      @keydown.delete='removeLastTag'
    />
  </div>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        tags: ['tag', 'input'],
        editable: false
      }
    },
    methods: {
      addTag(event) {
        let val = event.target.value
        if (val.length > 0) {
          this.tags.push(val)
          event.target.value = ''
        }
      },
      removeTag(index) {
        this.tags.splice(index, 1)
      },
      removeLastTag(event) {
        if (event.target.value.length === 0) {
          this.removeTag(this.tags.length - 1)
        }
      }
    }
  }
</script>

<style scoped>
  .container{
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    width:100%;
    height:100vh;
    background: linear-gradient(90deg, rgba(131,58,180,1) 0%, rgba(102,126,234,1) 50%, rgba(69,252,250,1) 100%);
  }
  
  a {
  position: absolute;
  right: 15px;
  bottom: 15px;
  font-weight: bold;
  text-decoration: none;
  color: #00003a;
  font-size: 20px;
}
  
  
/*tag input style*/
  
  .tag-input {
    width: 50%;
    border: 1px solid #D9DFE7;
    background: #fff;
    border-radius: 4px;
    font-size: 0.9em;
    min-height: 45px;
    box-sizing: border-box;
    padding: 0 10px;
    font-family: "Roboto";
    margin-bottom: 10px;
  }

  .tag-input__tag {
    height: 24px;
    color: white;
    float: left;
    font-size: 14px;
    margin-right: 10px;
    background-color: #667EEA;
    border-radius: 8px;
    margin-top: 10px;
    line-height: 24px;
    padding: 0 8px;
    font-family: "Roboto";
  }

  .tag-input__tag > span {
    cursor: pointer;
    opacity: 0.75;
    display: inline-block;
    margin-left: 8px;
  }

  .tag-input__text {
    border: none;
    outline: none;
    font-size: 1em;
  line-height: 40px;
  background: none;
  }

</style>
