<template>
  <h1>Add Project</h1>
  <form @submit.prevent="addProject">
      <label>Project Title</label>
      <input type="text" v-model="title">
      
      <label>Project Detail</label>
      <input type="text" v-model="detail">

      <button>Add project</button>
  </form>
</template>

<script>
export default {
    data() {
        return {
            title:"",
            detail:""
        }
    },
    methods: {
        addProject() {
            fetch('http://localhost:3000/projects', {
                method: 'POST',
                headers: {
                    "Content-Type": "application/json"
                },
                body: JSON.stringify(
                    {
                        title: this.title,
                        detail: this.detail,
                        complete: false
                    }
                )
            })
            .then(()=> {
                //redirect
                this.$router.push("/");
            })
            .catch((err)=> {
                console.log(err);
            })
        }
    }
}
</script>

<style>
    form {
        background-color: white;
        padding: 20px;
        border-radius: 10px;
    }
    label {
        display: block;
        text-transform: uppercase;
        font-weight: bold;
        color: darkslategrey;
        margin: 20px 0 10px 0;
        font-size: 14px;
        letter-spacing: 1px;
    }
    input {
        border: none;
        border-bottom: 1px solid dimgrey;
        padding: 10px;
        width: 100%;
        box-sizing: border-box;
        color: darkslategrey;
    }
    button {
        display: block;
        padding: 10px;
        border-radius: 10px;
        border: none;
        background-color: forestgreen;
        color: ghostwhite;
        margin: 25px auto 0;
        font-size: 16px;
        cursor: pointer;
    }
    button:hover {
        background-color: seagreen;
    }
</style>