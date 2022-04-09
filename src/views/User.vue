<template>
  <div class="main">
    <div class="profile">
      <Profile :user="this.user"/>
    </div>
    <div class="repositories">
      <ul class="repositories-menu">
        <li class="menu-item active" @click="changeActive($event), toogleActiveRepos()">
          Repos
          <span class="gray-circle">{{this.user.public_repos}}</span>
        </li>
        <li class="menu-item" @click="changeActive($event), toogleActiveStar()">
          Starred 
          <span class="gray-circle">{{this.userCountStarred}}</span>
        </li>
        <div class="indicator"></div>
      </ul>
      <div class="input-filter">
        <i class="fa fa-search" aria-hidden="true"></i>
        <input type="text" placeholder="Filter By Name" v-model="this.search">
      </div>
      <div v-if="this.isRepos">
        <div v-for="(repository, idx) in filterRepos" :key="idx" class="repos">
          <Repository :repos="repository"/>
        </div>
      </div>
      <div v-else-if="this.isStarred">
        <div v-for="(starred, idx) in filterStar" :key="idx" class="repos">
          <Starred :starred="starred"/>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import Profile from '../components/Profile.vue'
import Repository from '../components/Repository.vue'
import Starred from '../components/Starred.vue'

export default {
  data() {
    return {
      user: '',
      starred: '',
      userCountStarred: '',
      repos: '',
      search: '',
      isStarred: false,
      isRepos: true
    }
  },
  created() {
    axios.get(`https://api.github.com/users/${this.$route.params.username}`)
    .then(res => this.user = res.data)
    axios.get(`https://api.github.com/users/${this.$route.params.username}/starred`)
    .then(res => {
      this.starred = res.data
      this.userCountStarred = this.starred.length
    })
    axios.get(`https://api.github.com/users/${this.$route.params.username}/repos`)
    .then(res => {
      this.repos = res.data
    })
  },
  components: {
    Profile,
    Repository,
    Starred
  },
  methods: {
    changeActive(e) {
      const allLi = document.querySelectorAll('.menu-item')
      allLi.forEach( li => {
        if(li.classList.contains('active'))
          li.classList.remove('active')
      })

      if(e.target.nodeName == 'SPAN')
        e.path[1].classList.add('active')
      else  
        e.target.classList.add('active')
    },
    toogleActiveRepos() {
      if(!this.isRepos){
        this.isRepos = !this.isRepos
        this.isStarred = !this.isStarred
      }
    },
    toogleActiveStar() {
      if(!this.isStarred){
        this.isRepos = !this.isRepos
        this.isStarred = !this.isStarred
      }
    }
  },
  computed: {
    filterRepos() {
      return this.repos.filter( repos => {
        return repos.name.match(this.search.toLowerCase())
      })
    },
    filterStar() {
      return this.starred.filter( repos => {
        return repos.name.match(this.search.toLowerCase())
      })
    }
  }
}
</script>

<style scoped>

.main {
  display: flex;
  min-width: 100%;
  min-height: calc(100vh - 50px);
}

.profile {
  width: 30%;

}

.repositories {
  width: 60%;
}

.repos {
  width: 85%;
  margin: 0 5%;
}

.repositories-menu {
  display: flex;
  gap: 20px;
  margin-top: 20px;
  position: relative;
}

.menu-item {
  display: flex;
  align-items: center;
  gap: 5px;
  width: 25%;
  justify-content: center;
  font-size: 1.1em;
  color: rgb(75, 75, 75);
}

.indicator {
  position: absolute;
  top: 30px;
  width: 25%;
  border-bottom: 4px solid rgb(231, 130, 42);
  transition: 0.3s;
}

.gray-circle {
  border-radius: 50%;
  background-color: rgb(209, 209, 209);
  width: 25px;
  height: 25px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.input-filter {
  display: flex;
  height: 30px;
  width: 50%;
  margin: 50px 0;
  align-items: center;
}

.input-filter i {
  display: flex;
  height: 100%;
  align-items: center;
  padding: 0 10px;
  color: rgb(158, 158, 158);
  border: 1px solid rgb(158, 158, 158);
  border-right: none;
  border-radius: 5px 0 0 5px;
}

.input-filter input {
  width: 100%;
  height: 100%;
  outline: none;
  border: 1px solid rgb(158, 158, 158);
  border-left: none;
  border-radius: 0 5px 5px 0;
}

.repositories ul li:nth-child(1).active ~.indicator {
  transform: translateX(calc(calc(50% + 10px) * 0));
}

.repositories ul li:nth-child(2).active ~.indicator {
  transform: translateX(calc(calc(100% + 10px) * 1));
}

@media (max-width: 800px) {
 
.main {
  display: flex;
  flex-direction: column;
  min-width: 100%;
  min-height: calc(100vh - 50px);
}

.profile {
  width: 100%;
}

.repositories {
  width: 100%;
  max-width: 100%; 
}

.repositories-menu {
  width: 100%; 
}

.menu-item {
  display: flex;
  align-items: center;
  width: 50%;
  justify-content: center;
  font-size: 1.1em;
  color: rgb(75, 75, 75);
}

.indicator {
  position: absolute;
  top: 30px;
  width: calc(50% - 10px);
  border-bottom: 4px solid rgb(231, 130, 42);
  transition: 0.3s;
}

.repositories ul li:nth-child(1).active ~.indicator {
  transform: translateX(calc(calc(50% + 10px) * 0));
}

.repositories ul li:nth-child(2).active ~.indicator {
  transform: translateX(calc(calc(100% + 20px) * 1));
}

.input-filter {
  display: flex;
  height: 30px;
  width: 80%;
  margin: 10%;
  align-items: center;
}

}

</style>