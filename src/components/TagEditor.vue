<template>
<div>
  <div class='tag-input'>
    <div class='tag-input-tags'>
      <button @click="removeAll">
        clear all
      </button>

      <ul>
        <li v-for='tag in tags' :key='tag'>
          <Tags :tag="tag" @removeTag="removeTag(index)"/>
        </li>
      </ul>
    </div>

    <input
      placeholder="Enter a Tag"
      class='tag-input-text'
      @keydown.enter='addTag'
      @keydown.188='addTag'
      @keydown.delete='removeLastTag'
    />
  </div>
  </div>
</template>

<script>
import Tags from '@/components/Tags'

  export default {
    name: "TagEditor",
    components: {
      Tags
    },
    data() {
      return {
        tags: [
          {title: 'tag1'},
          {title: 'tag2'},
          {title: 'tag3'},
          {title: 'tag4'}
        ],
      }
    },
    methods: {
      addTag(event) {
        let val = event.target.value
        if (val.length > 0) {
          this.tags.push({title: val})
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
      },
      removeAll () {
        this.tags = []
      }
    }
  }
</script>

<style>
  body {
    background:lightgrey
  }
  .tag-input {
    display: flex;
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

  .tag-input li {
    height: 24px;
    color: black;
    float: left;
    font-size: 14px;
    margin-right: 10px;
    background-color: lightgrey;
    border-radius: 8px;
    line-height: 24px;
    padding: 0 8px;
    font-family: "Roboto";
    list-style-type: none;
  }

  .tag-input-tags > span {
    cursor: pointer;
    opacity: 0.75;
    display: inline-block;
    margin-left: 8px;
  }
  .tag-input-tags {
    display:flex;
    align-items: center;
  }
    
  .tag-input-text {
    border: none;
    outline: none;
    font-size: 1em;
    line-height: 40px;
    background: none;
  }
  .tag-input button {
    background: transparent;
    border: 1px solid lightgray;
    border-radius: 15px;
    height: min-content;
    padding: 6px;
  }
</style>
