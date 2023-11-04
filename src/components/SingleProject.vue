<template>
    <div class="projects" :class="{complete : project.complete}">
    <div class="actions">
      <h3  @click="showDetail">{{ project.title }}</h3>
        <div class="icons">
            <RouterLink :to="{name:'EditProject', params: { id : project.id }}">
            <span class="material-icons">edit</span>
            </RouterLink>
            <span @click="deleteProject" class="material-icons">delete</span>
            <span @click="completeProject" class="material-icons tick">done</span>
        </div>
    </div>
    <div v-if="showDetails" class="details">
        {{project.details }}
        </div>
    </div>
</template>

<script>
export default{
    props:['project'],
    data(){
        return{
            showDetails: false,
            urlThis: "http://localhost:3000/projects/" + this.project.id,
        }
    },
    methods:{
        showDetail(){
            this.showDetails = !this.showDetails
        },
       deleteProject(){
        fetch(this.urlThis, { method: "DELETE" }).then(() =>
        this.$emit("delete", this.project.id));
       } ,
       completeProject(){
        fetch(this.urlThis, {
        method: "PATCH",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify({ complete: !this.project.complete }),
      })
        .then(() => this.$emit("complete", this.project.id))
        .catch((err) => console.log(err.name));
    },
       }
    }
</script>

<style>
.projects {
    margin: 20px auto;
    background-color: #fcd730;
    padding:0px 20px;
    /*box-shadow: 1px 2px 3px rgba(0, 0, 0, 0.5);
    border-left: 10px solid red;*/
    box-shadow: -7px 6px #000;
    max-width: 400px;
  }
  h3 {
    cursor: pointer;
    color: black;
    font-family:'Courier New', Courier, monospace;
  }
  .actions {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  .details{
       color:#000;
       font-family:Verdana, Geneva, Tahoma, sans-serif;
       font-size: smaller;
       padding-bottom: 10px;
  }
  
  .material-icons {
    font-size: 25px;
    margin-left: 10px;
    font-weight: bold;
    cursor: pointer;
    color: #827c6a;
  }
  .material-icons:hover {
    color: black;
  }
  .projects.complete {
    text-decoration: line-through black;
  }
  .projects.complete .tick{
    color: black;
  }
</style>