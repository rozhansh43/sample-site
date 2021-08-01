<template>
  <div>
    <span @click="clicked" v-show="!editable">
      {{ tag.name }}
    </span>

    <input 
    type="text" 
    v-show="editable" 
    v-model="tag.name" 
    @keyup.enter="saved"
    />  

    <span v-if="this.editable == false" @click='removeTag(tag.id)'>
      x
    </span>
    <span v-else @click='removeTag(tag.id)'>
      >
    </span>
  </div>
</template>

<script>
export default {
    name: 'Tags',
    props: {
      tag: { type: String },
      editable: { type: Boolean },
    },
    data () {
      return {
      }
    },
    methods: {
      clicked () {
        this.editable = true
      },
      saved () {
        this.editable = false
      },
      removeTag (tagId) {
        if ( this.editable == true ) {
          this.editable = false
        }else {
          this.$emit('removeTag', tagId);
        }
      }
    }
}
</script>
