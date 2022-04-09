<template>
  <div class="home">
    <form @submit.prevent.stop="buscaPerfilGit()" class="main-form">
      <div class="form-group">
        <i class="fa fa-search" aria-hidden="true"></i>
        <input type="text" placeholder="Insert a Username" v-model="this.username">
      </div>
    </form>
  </div>
</template>

<script>

export default {
  data() {
    return {
      username: '',
      a: 0
    }
  },
  methods: {
    buscaPerfilGit() {
      this.$router.push(`/user/${this.username}`)
    }   
  }
}
</script>

<style scoped>

.main-form {
  display: flex;
  min-width: 100vw;
  min-height: calc(100vh - 50px);
  justify-content: center;
}

.form-group {
  display: flex;
  min-width: 250px;
  width: 30%;
  height: 30px;
  margin-top: 50px;
  align-items: center;
}

.fa-search {
  display: flex;
  height: 100%;
  align-items: center;
  padding: 0 10px;
  color: rgb(158, 158, 158);
  border: 1px solid rgb(158, 158, 158);
  border-right: none;
  border-radius: 5px 0 0 5px;
}

.fa-search:hover {
  cursor: pointer;
}

.form-group input {
  width: 100%;
  height: 100%;
  outline: none;
  border: 1px solid rgb(158, 158, 158);
  border-left: none;
  border-radius: 0 5px 5px 0;
  font-weight: 700;
  color: rgb(107, 107, 107);
}

::placeholder {
  font-weight: 700;
  color: rgb(107, 107, 107);
}

</style>
