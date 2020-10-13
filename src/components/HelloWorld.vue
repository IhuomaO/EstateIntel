<template>
  <div class="container">
      <form>
          <div class="topNav">
            <div class="header" >
              <div class='caption'>
                Ongoing Projects
              </div>
              <div class="form-group form-inline">
                  <input class="form-control" type="text" name="searchTerm" placeholder="Search History"/>
              </div>
            </div>

          
              <div class='unique'>
                Select Preferred Columns
              </div>
              <div class='btn-feild'>
                <div class="btn-group caption" role="group" aria-label="Button group with nested dropdown">
                  <button type="button" class="btn btn-secondary">Main Contractor</button>
                  <button type="button" class="btn btn-secondary">Area</button>
                  <button type="button" class="btn btn-secondary">State</button>
                  <button type="button" class="btn btn-secondary">Status</button>
                  <button type="button" class="btn btn-secondary">Sector</button>
                  <button type="button" class="btn btn-secondary">Country</button>
                  <button type="button" class="btn btn-secondary">Address</button>
                  <button id="btnGroupDrop1" type="button" class="btn btn-secondary dropdown-toggle" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
                      View More
                    </button>
                </div>

                <div class="btn-group form-group" role="group">
                  <button id="btnGroupDrop1" type="button" class="btn btn-secondary dropdown-toggle" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
                    
                  </button>
                </div>
              </div>

            <div class="icons">
              <div class='Ficons'>1000 Projects</div>
              <div class="Bicons">
                  <span class='counter caption'>1-50 of 500</span>
                  <label class="switch form-group">
                    <input type="checkbox">
                    <span class="slider round"></span>
                  </label>
              </div>
            </div>

          </div>

          <table class="table table-striped">
            <thead>
            <tr>
              <th scope="col">Project Name</th>
              <th scope="col">Developer</th>
              <th scope="col">Main Contractor</th>
              <th scope="col">Area</th>
              <th scope="col">State</th>
              <th scope="col">Status</th>
              <th scope="col">Sector</th>
            </tr>
            </thead>
            <tbody v-for="(project) in projects" :key="project.id">
              <tr >
                <td> {{project.project_name}} </td>
                <td> {{project.developer}} </td>
                <td> {{project.main_contractor}} </td>
                <td> {{project.lga}} </td>
                <td> {{project.state}} </td>
                <td> {{project.status}} </td>
                <td> {{project.sector}} </td>
              </tr>
            </tbody>
          </table>

      </form>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';

@Component
export default class HelloWorld extends Vue {
          private projects: any=[]; 
          private  fetchUsers () {
              const baseURI = 'https://70c5b72c-65db-4a66-ba01-3e14763157e8.mock.pstmn.io'
              Vue.prototype.$http.get(baseURI)
              .then((result: any) => {
                this.projects = result.data.data;
              })
            }
  created () {
    this.fetchUsers();
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.container {
  background-color: ghostwhite;
  
.topNav {
  overflow-x:hidden;
}

thead {
  background-color: black;
}

table {
 margin-top: 1.5rem;
 overflow-x: scroll;
 overflow-y: scroll;
}

th {
  color: azure;
  font-size: small;
  font-weight: normal;
}

td {
  color: black;
  font-size: smaller;
  font-weight: normal;
}
.header {
  width: 100%;
  padding-top: 1em;
   margin-bottom: 3rem;
}

.btn-feild {
  width: 100%;
  padding-top: 0.5em;
  margin-bottom: 2rem;
}

.form-group {
  float: right;
}

.caption {
  float: left;
  
}

.unique {
  width:100%;
  display: block;
  font-size: smaller;
  padding-top: 2em;
  text-align: left;
  margin-bottom: 0.5rem;
}

.icons {
  width: 100%;
  margin-top: 2em;
  display: flex;
  font-size: smaller;
  margin-bottom: 0.5rem;
}

.Ficons {
  font-size: smaller;
  width: 50%;
  text-align: left;


}

.Bicons {
  font-size: smaller;
   width: 50%;

}

.counter {
  font-size: smaller;
}


.btn {
  margin-right: 0.25em;
  font-size: smaller;
  background-color: transparent;
  color: black;
}

/* The switch - the box around the slider */
.switch {
  position: relative;
  display: inline-block;
  width: 50px;
  height: 32px;
}

/* Hide default HTML checkbox */
.switch input {
  opacity: 0;
  width: 0;
  height: 0;
}

/* The slider */
.slider {
  position: absolute;
  cursor: pointer;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: #ccc;
  -webkit-transition: .4s;
  transition: .4s;
}

.slider:before {
  position: absolute;
  content: "";
  height: 20px;
  width: 20px;
  left: 4px;
  bottom: 4px;
  background-color: white;
  -webkit-transition: .4s;
  transition: .4s;
}

input:checked + .slider {
  background-color: black;
}

input:focus + .slider {
  box-shadow: 0 0 1px black;
}

input:checked + .slider:before {
  -webkit-transform: translateX(26px);
  -ms-transform: translateX(26px);
  transform: translateX(26px);
}

/* Rounded sliders */
.slider.round {
  border-radius: 34px;
}

.slider.round:before {
  border-radius: 50%;
}

}

@media only screen and (max-width: 600px) {
  .btn-feild .header .unique {
    display: hidden;
  }
}

</style>
