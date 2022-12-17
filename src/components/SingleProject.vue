<template>
  <div class="project" :class="{complete: project.complete}">
      <div class="flexbox">
          <div >
              <h3 @click="showDetail = !showDetail">{{project.title}}</h3>
          </div>
          <div>
                <span class="material-icons" @click="updateCompleteProject">
                    done
                </span>
                <router-link :to="{name: 'EditProject', params:{id: project.id}}">
                    <span class="material-icons">
                        edit
                    </span>
                </router-link>
                <span class="material-icons" @click="deleteProject">
                    delete
                </span>
          </div>
      </div>
      <p v-if="showDetail">{{project.detail}}</p>
  </div>
</template>

<script>
export default {
    props: ['project'],
    data() {
        return {
            showDetail: false,
            api: 'http://localhost:3000/projects/'
        }
    },
    methods: {
        deleteProject() {
            let deleteRoute = this.api + this.project.id;
            fetch(deleteRoute, {method: 'DELETE'})
            .then(() => {
                this.$emit("delete", this.project.id)
            })
            .catch((err) => {
                console.log(err.message())
            })
        },
        updateCompleteProject() {
            let updateCompleteRoute = this.api + this.project.id;
            fetch(updateCompleteRoute, 
            {
                method: "PATCH",
                headers: {
                    "Content-Type": "application/json"
                },
                body: JSON.stringify(
                    {
                        complete: !this.project.complete
                    }
                )
            }
            )
            .then(() => {
                this.$emit("complete", this.project.id)
            })
            .catch((err) => {
                console.log(err.message())
            })
        }
    }
}
</script>

<style>
    .project {
        padding: 30px;
        background-color: aliceblue;
        margin: 10px;
        border-radius: 10px;
        border-left: 7px solid crimson;
    }
    h3 {
        color: darkslategrey;
        cursor: pointer;
    }
    h3:hover {
        color: teal;
    }
    .flexbox {
        display: flex;
        justify-content: space-between;
        align-items: center;
    }
    span {
        margin: 5px;
    }
    span:hover {
        color: dimgrey;
        cursor: pointer;
    }
    .complete {
        border-left-color: forestgreen;
    }
</style>