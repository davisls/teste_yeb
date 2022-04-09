<template>
    <div>
        <div class="profile">
            <img :src="this.user.avatar_url" class="user-img">
            <div class="flex-d">
                <p class="user-name">{{this.user.name}}</p>
                <p class="user-bio">{{this.user.bio}}</p>
                <p class="user-local">{{this.user.location}}</p>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {

        }
    },
    props: {
        user: Object
    }
}
</script>

<style scoped>

.profile {
    margin-top: 20px;
    display: flex;
    flex-direction: column;
    align-items: center;
    text-align: center;
    width: 100%;
}

.user-img {
    width: 60%;
    min-width: 100px;
    height: 60%;
    min-height: 100px;
    border-radius: 50%;
    margin: 10px 0;
}

.user-name {
    color: rgb(73, 73, 73);
    font-size: 1.3em;
    margin: 10px 0;
}

.user-bio {
    color: #000;
    font-size: 1em;
    margin-bottom: 10px;
}

.user-local {
    color: rgb(48, 48, 48);
    font-size: 1em;
}

@media (max-width: 800px) {

.profile {
    margin-top: 20px;
    display: flex;
    flex-direction: row;
    align-items: center;
    text-align: center;
} 

.user-img {
    width: 20%;
    min-width: 80px;
    height: 20%;
    min-height: 80px;
    border-radius: 50%;
    margin: 3px;
} 

.flex-d {
    display: flex;
    flex-direction: column;
    width: 50%;
    min-width: 80px;
    margin-right: 10px;
}

.user-name {
    color: rgb(73, 73, 73);
    font-size: 0.9em;
    margin: 10px 0;
}

.user-bio {
    color: #000;
    font-size: 0.8em;
    margin-bottom: 10px;
}

.user-local {
    color: rgb(48, 48, 48);
    font-size: 0.8em;
}

}

</style>