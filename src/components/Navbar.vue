<template>
    <div class="">
        <div class="navbar">
            <span class="nav-logo">
                <i class="fa fa-github fa-2x" aria-hidden="true"></i>
                <h3>Github</h3>
                <h3>profiles</h3>
            </span>
            <span class="change-username">
                <button @click="home()" class="change">
                    Change Username
                </button>
            </span>
        </div>
    </div>
</template>

<script>
export default {
    methods: {
        home() {
            this.$router.push('/')
        }
    }
}
</script>

<style scoped>

.navbar {
    position: relative;
    display: flex;
    min-width: 100%;
    height: 50px;
    background-color: rgb(49, 49, 49);
}

.nav-logo {
    display: flex;
    height: 100%;
    align-items: center;
    margin-left: 20px;
    gap: 5px;
    color: #FFF
}

.nav-logo h3 {
    letter-spacing: 0.3px;
}

.fa-github {
    margin-right: 10px;
}

.change-username {
    position: absolute;
    right: 10px;
}

.change {
    margin-top: 10px;
    display: flex;
    height: 30px;
    align-items: center;
    border: 1px solid white;
    border-radius: 8px;
    padding: 3px;
    font-size: 1em;
    outline: none;
    background: none;
    color: #FFF;
    transition: 0.3s;
}

.change:hover {
    cursor: pointer;
    background-color: #FFF;
    color: rgb(49, 49, 49);
}

@media (max-width: 800px) {

.nav-logo {
    margin-left: 10px;
    gap: 5px;
}

.fa-github {
    margin-right: 0px;
}

.nav-logo h3 {
    font-size: 0.7em;
    letter-spacing: 0.2px;
}

.change { 
    font-size: 0.7em;
}

}

</style>