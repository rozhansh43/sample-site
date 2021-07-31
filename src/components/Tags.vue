<template>
  <div>
    <span @click="clicked" v-show="!ineditmode">
    {{ tag.name }}
    </span>

    <input 
    type="text" 
    v-show="ineditmode" 
    v-model="tag.name" 
    @keyup.enter="saved"
    />  

    <span @click='removeTag(tag.id)'>
      x
    </span>
  </div>
</template>

<script>
export default {
    name: 'Tags',
    props: {
      tag: { type: Array, default: () => [] }
    },
    data () {
        return {
          ineditmode: false
        }
    },
    methods: {
      clicked () {
        this.ineditmode = true
      },
      saved () {
        this.ineditmode = false
      },
      removeTag(tagId) {
        this.$emit('removeTag', tagId);
        this.ineditmode = false
      }
    }
}
</script>
