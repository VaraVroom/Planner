<template>
    <form @submit.prevent="projectSubmit">
      <label>Title:</label>
      <input type="text" v-model="title" required />
      <br />
      <br />
      <label>Details:</label>
      <textarea v-model="details" required></textarea>
      <br />
      <br />
      <button>Add Project</button>
    </form>
  </template>
  
  <script>
  export default {
    data() {
      return {
        title: "",
        details: "",
      };
    },
    methods: {
      projectSubmit() {
        let newProject = {
          title: this.title,
          details: this.details,
          complete: false,
        };
        fetch("http://localhost:3000/projects", {
          method: "POST",
          headers: { "Content-Type": "application/json" },
          body: JSON.stringify(newProject),
        })
          .then(() => this.$router.push("/homePage"))
          .catch((err) => console.log(err.name));
      },
    },
  };
  </script>

<style>
form {
  background-color: white;
  padding: 20px;
  margin-top: 20px;
  border-radius: 10px;
  border-color: black;
  border-style:solid;
}
label {
  display: block;
  color: black;
  font-size: 15px;
  font-weight: bold;
  text-transform: uppercase;
  letter-spacing: 1px;
  margin: 20px 0 10px 0;
}
input {
  padding: 10px;
  border: 2px solid;
  width: 100%;
  box-sizing: border-box;
  border-color: black;
  border-style:solid;
}

textarea {
  padding: 10px;
  border: 2px solid #ddd;
  width: 100%;
  height: 100px;
  box-sizing: border-box;
  border-color: black;
  border-style:solid;
}

form button{
  text-decoration:none;
  color:#000;
  margin:auto;
  width:150px;
  display:inline-block;
  line-height:40px;
  font-size:12px;
  font-weight:900;
  letter-spacing:2px;
  text-transform:uppercase;
  background-color: #fdd018;
   border:2px solid #000;
   box-shadow:0px 0px 0, 1px 1px 0, 2px 2px 0, 3px 3px 0,4px 4px 0;
  position: relative;
}

form button:after{
  content: "";
  position: absolute;
  left: 0;
  top: 0;
  height: 100%;
  width:100%;
   z-index: -1;
  background-color: #fff;
  transition: all 0.5s;
  -webkit-transition: all 0.5s;
  -moz-transition: all 0.5s;
  -ms-transition: all 0.5s;
  -o-transition: all 0.5s;
}
form button:hover{
  background-color: #fdd017;
}
 form button:hover:after{
  background-color: #f5de57;
}

 form button:active{
   top:5px;
   left:5px;
   box-shadow:0 0 0 0;
}
</style>