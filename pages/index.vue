<template>
  <main>
    <div class="header">
      <div class="divider"></div>
        <h1>AlefiDev - ListTask</h1>
        <p>- Crie sua lista de tarefas</p>
        <div class="social">
          <a href="https://github.com/Alef185" target="_blank"><img src="images/github.png" alt=""></a>
          <a href="https://www.linkedin.com/in/alef-souza-rosa/" target="_blank"><img src="images/linkedin.png" alt=""></a>
          <a href="https://www.instagram.com/alef_eu/" target="_blank"><img src="images/instagram.png" alt=""></a>
        </div>
        <div class="divider"></div>
    </div>
    <div class="create-new">
      <input 
        type="text"
        v-model="newTask" 
        placeholder="Adicionar nova tarefa" 
        @keypress.enter="addTask" />
        <button @click="addTask">+</button>
    </div>

    <div class="tasks">
      <Task
        v-for="(task, i) in $store.state.tasks"
        :key="i"
        :task="task"/>
    </div>
    <div class="icon">AlefiDev - 2022 <a href="https://alef-rosa.vercel.app" title="Portfólio" target="_blank">[Portfólio]</a>
    <div class="icon2">Ícones feitos por <a href="https://www.flaticon.com/br/autores/google" title="Google">Google</a> from <a href="https://www.flaticon.com/br/" title="Flaticon">www.flaticon.com</a></div>
    </div>
  </main>
</template>

<script>
export default {
  data (){
    return {
      newTask: ''
    }
  },
  methods: {
    addTask () {
      if (this.newTask) {
        this.$store.commit('ADD_TASK', this.newTask);
        this.newTask = '';
      }
    }
  }
}
</script>
