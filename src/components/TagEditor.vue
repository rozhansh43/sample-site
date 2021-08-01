<template>
  <div>
    <b-input-group prepend="تگ" class="mt-3 tag-input">
      <b-form-input
        placeholder="افزودن تگ"
        class='tag-input-text'
        @keydown.enter='addTag(name)'
        @keydown.delete='removeLastTag'
        maxlength="4" 
        v-model="name"
      />
        
      <b-input-group-append>
        <span class="d-flex align-items-center mx-2">
         4 / {{ name.length }} 
        </span>

        <b-button variant="info" @click="addTag(name)">
          {{ "افزودن" +  " +" }}
        </b-button>
      </b-input-group-append>
    </b-input-group>

    <div class='tag-input-tags'>
      <b-button @click="removeAll">
        پاک کردن همه
      </b-button>
      
      <ul>
        <li v-for='tag in tags' :key='tag'>
          <tags :tag="tag" :editable="editable" @removeTag="removeTag"/>
        </li>
      </ul>

      <span class="mx-3" >
        6 / {{ tags.length }}
      </span>
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
        editable: false,
        name: "",
        tags: [
          { 
            id: String(Math.floor(Math.random() * 999999999)),
            name: 'tag1'
          },
          {
            id: String(Math.floor(Math.random() * 999999999)),
            name: 'tag2'
          },
          {
            id: String(Math.floor(Math.random() * 999999999)),
            name: 'tag3'
          },
          {
            id: String(Math.floor(Math.random() * 999999999)),
            name: 'tag4'
          }
        ],
      }
    },
    methods: {
      addTag(name) {
      if (this.tags.map((e) => e.name).includes(name)) {
        return;
      }
      if (this.tags.length < 6 && name.length > 1 ) {
        this.tags.push({
          id: String(Math.floor(Math.random() * 999999999)),
          name,
        });
        this.name = "";
        }
      },
      removeTag (tagId) {
        this.tags = this.tags.filter(o => o.id !== tagId)
      },
      removeLastTag () {
        if ( this.name == 0 ) {
          this.tags.pop()
        }
      },
      removeAll () {
        this.tags = []
      }
    }
  }
</script>

<style>
  .tag-input {
    border: 1px solid #D9DFE7;
    background: #fff;
    border-radius: 4px;
    box-sizing: border-box;
    margin-bottom: 10px;
    width: 100%;
  }

  .tag-input input {
    border:none
  }

  .tag-input-tags ul {
    margin: 0!important;
  }

  .tag-input-tags li input{
    text-align: center;
    border: none;
    border-radius: 5px;
  }

  .tag-input-tags li {
    color: black;
    float: left;
    margin-right: 10px;
    background-color: lightgrey;
    border-radius: 17px;
    line-height: 24px;
    padding: 4px 14px;
    list-style-type: none;
  }

  .tag-input-tags > span {
    cursor: pointer;
    opacity: 0.75;
    margin-left: 8px;
  }
  .tag-input-tags {
    display: flex;
    align-items: center;
    padding-top: 10px;
    padding-bottom: 10px;
  }

  .tag-input-tags button{
    margin-right:5px
  }
    
  .tag-input-text {
    border: none;
    outline: none;
    line-height: 40px;
    background: none;
    width: 79%;
    padding-right: 8px;
  }
  .tag-input-tags button {
    background: transparent;
    border: 1px solid lightgray;
    border-radius: 15px;
    height: min-content;
    padding: 6px;
  }
</style>
