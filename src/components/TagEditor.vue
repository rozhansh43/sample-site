<template>
  	
	<div class="container" id="todo">
			
			<section class="panel">	

				<input type="checkbox" id="mark-all" @click="selectAll" :checked="areAllSelected">
				<input v-model="newTask" @keyup.enter="addTask" placeholder="What do you need to do?" autofocus class="text-input">
        <ul class="list-item">

					<li v-for="task in tasks" :class="{done: isChecked(task)}" :key="task.index">

						<input type="checkbox" class="checkbox" @click="check" v-model="task.checked">
						
						<input type="text" v-if="task === editingTask" v-auto-focus class="text-input" @keyup.enter="endEditing(task)" @blur="endEditing(task)" v-model="task.text">

						<label for="checkbox" v-if="task !== editingTask" @dblclick="editTask(task)">{{ task.text }}</label>
						
						<button class="delete" @click="removeTask(task)">X</button>

					</li>
				
				</ul>
				<button @click="clearList">Clear List</button>
        
			</section>
	</div>
</template>

<script>
export default {		
  data () {
    return {
    }
  },
  		
}
</script>

<style>

</style>