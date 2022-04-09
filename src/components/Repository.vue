<template>
    <div>
       <p class="name">{{this.repos.name}}</p> 
       <p class="description">{{this.repos.description}}</p> 
       <p class="info">
           <span>
               <i class="fa fa-angle-left" aria-hidden="true"></i>
               <i class="fa fa-angle-right" aria-hidden="true"></i>
               {{this.repos.language}}
            </span>
            <span>
                <i class="fa fa-code-fork" aria-hidden="true"></i>
               {{this.repos.forks}}
            </span>
        </p> 
        <p class="linha"></p>
    </div>
</template>

<script>
export default {
    data() {
        return {

        }
    },
    props: {
        repos: Object
    }
}
</script>

<style scoped>

.name {
    color: rgb(40, 170, 206);
    font-size: 1.3em;
    margin-bottom: 10px;
}

.description {
    color: rgb(53, 53, 53);
    font-size: 1em;
    margin-bottom: 10px;
    word-break: break-word;
}

.info {
    display: flex;
    gap: 20px;
}

.linha {
    margin: 15px 0;
    border-bottom: 1px solid gainsboro;
    width: 100%;
}

</style>