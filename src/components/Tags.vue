<template>
  <div>
       <span @click="clicked" v-show="!ineditmode">
        {{ tag.title }}
      </span>

      <input type="text" v-show="ineditmode" v-model="tag.title" @keyup.enter="saved"/>  

        <span @click='removeTag'>
          x
        </span>
  </div>
</template>

<script>
export default {
    name: 'Tags',
    props: ['tag'],
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
      removeTag() {
        this.$emit('removeTag');
      }
    }
}
</script>

<style>

</style>