<template>
  <div class="container-fluid" style="border-top: 2px solid #d9d9d9">
        <div class="row g-2 mt-3">
            <div class="col-lg-6">
              <h1 class="m-0 font-weight-bold text-black-50 text-start">Users</h1>
            </div>
            <div class="col-lg-6 text-end">
              <button id="new-user" class="btn btn-lg btn-primary">+ New User</button>

            </div>
        </div>

        <!-- filter -->
        <div class="card-body" id="accordion">

             <div class="card">
                <div class="card-header mouse-pointer text-end" id="headingOne" data-bs-target="#collapseOne" aria-bs-expanded="true" aria-bs-controls="collapseOne" data-bs-toggle="collapse">
                    <span class="fa fa-filter"></span>
                    Filter
                </div>

                  <div id="collapseOne" class="collapse show" aria-bs-labelledby="headingOne" data-bs-parent="#accordion">
                        <div class="card-body">

                             <div class="row g-2 mb-3">
                                 
                                <div class="col-md-6">
                                    <div class="form-floating">
                                        <input type="text" class="form-control" id="firstNameFilter" v-model="firstNameFilter" placeholder="First Name" autocomplete="off">
                                        <label for="firstNameFilter">First Name</label>
                                    </div>
                                </div>

                                <div class="col-md-6">
                                    <div class="form-floating">
                                        <input type="text" class="form-control " id="lastNameFilter" v-model="lastNameFilter" placeholder="Last Name" autocomplete="off">
                                        <label for="lastNameFilter">Last Name</label>
                                    </div>
                                </div>

                             </div>

                             <div class="row g-2 mb-3">
                                 
                                <div class="col-md-4">
                                    <div class="form-floating">
                                        <input type="text" class="form-control " id="emailFilter" v-model="emailFilter" placeholder="E-mail" autocomplete="off">
                                        <label for="emailFilter">E-mail</label>
                                    </div>
                                </div>

                                <div class="col-md-4">
                                    <div class="form-floating">
                                        <input type="text" class="form-control " id="phoneNumberFilter" v-model="phoneNumberFilter" placeholder="Phone Number" autocomplete="off">
                                        <label for="phoneNumberFilter">Phone Number</label>
                                    </div>
                                </div>

                                <div class="col-md-4">
                                    <div class="form-floating">
                                        <OptionComponent id="statusFilter" :options="options" :selectedStatusFilter="selectedStatusFilter"/>
                                        <label for="statusFilter">Status</label>
                                    </div>
                                </div>

                             </div>
                                                          
                            <div class="row g-2 mt-3">
                                <div class="col-lg-6 col-md-12 col-sm-12">
                                    <div class="align-self-end">
                                        <div class="form-group">
                                            <input type="button" value="Search" class="btn btn-lg btn-primary me-2" />
                                            <input type="submit" value="Clear Filters" class="btn btn-lg btn-primary" />
                                        </div>
                                    </div>
                                </div>
                            </div>

                        </div>

                  </div>

             </div>

        </div>

        <div class="card-body">

             <div class="d-flex justify-content-center">
                 <div id="spinner" class="spinner-border text-primary" role="status" style="display:none;">
                     <span class="sr-only">Loading</span>
                 </div>
            </div>

            <!-- table -->
            <table class="table table-striped">
                <thead>
                    <tr>
                        <th scope="col"></th>
                        <th scope="col"></th>
                        <th scope="col">First Name</th>
                        <th scope="col">Last Name</th>
                        <th scope="col">E-mail</th>
                        <th scope="col">Phone Number</th>
                        <th scope="col">Status</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td><a class="btn btn-primary" href="#"><i class="fa fa-edit"></i></a></td>
                        <td><a class="btn btn-danger" href="#"> <i class="fa fa-user-times"></i></a></td>
                        <td>Mark</td>
                        <td>Otto</td>
                        <td>jalter_roberto@hotmail.com</td>
                        <td>16 997510595</td>
                        <td>Active</td>
                    </tr>
                    <tr>
                        <td><i class="fa fa-edit"></i></td>
                        <td><i class="fa fa-user-times"></i></td>
                        <td>Mark</td>
                        <td>Otto</td>
                        <td>jalter_roberto@hotmail.com</td>
                        <td>16 997510595</td>
                        <td>Active</td>
                    </tr>
                    
                </tbody>
            </table>                

        </div>
    </div>
</template>

<script>
import OptionComponent from './OptionComponent.vue'

export default {

  name: "UsersIndex",

  data() {
    return {
      id: "",
      users: [],
      firstNameFilter: "",
      lastNameFilter: "",
      emailFilter: "",
      phoneNumberFilter: "",
      options: [
				{ text: "Active", value: "1"},
				{ text: "Inactive", value: "2"},
			],
	  selectedStatusFilter: 0
    };
  },
  methods :{
    async getAllUsers(){
        // let token = 'Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJVc2VySWQiOiI0IiwiVXNlck5hbWUiOiJqYWx0ZXIuZGFzaWx2YUBzdGdlbi5jb20iLCJGaXJzdE5hbWUiOiJKYWx0ZXIiLCJMYXN0TmFtZSI6ImRhIFNpbHZhIiwiQ3VycmVudEhlcmRDb2RlIjoiOTkwMTAxOTciLCJGYXJtSWQiOiI5OTAxMDE5NyIsIkhlcmRDb2RlIjoiOTkwMTAxOTciLCJGYXJtTmFtZSI6IlNhcmEncyBUZXN0IEhlcmQiLCJGYXJtT3duZXJOYW1lIjoiU2FyYSdzIFRlc3QgSGVyZCIsIkZhcm1DaXR5IjoiVmFpbCIsIkZhcm1TdGF0ZSI6IkFaIiwiRmFybUNvdW50cnkiOiJVbml0ZWQgU3RhdGVzIiwiRmFybUVtYWlsIjoiIiwiVXNlclJvbGVJZCI6IjEiLCJodHRwOi8vc2NoZW1hcy5taWNyb3NvZnQuY29tL3dzLzIwMDgvMDYvaWRlbnRpdHkvY2xhaW1zL3JvbGUiOiJBZG1pbmlzdHJhdG9yIiwianRpIjoiNWE3YmRmYTItZmQwNC00ZGFmLWExY2YtMjlhNmJkNjY5MzZjIiwiZXhwIjoxNjUwNTc2MTE4fQ.ERpqzLX5H6obVmwKJ5fXyD4Hky60lvpsYIM2wAR78oU';        
        // localStorage.setItem( 'token', JSON.stringify(token) );

        var auth = JSON.parse(localStorage.getItem( 'token'));

        const req = await fetch(`https://localhost:44325/User?firstName=${this.firstNameFilter}&lastName=${this.lastNameFilter}&email=${this.emailFilter}&phoneNumber=${this.phoneNumberFilter}&filterActive=${this.selectedStatusFilter}`, {
               method: 'GET',
               headers: {
                   Accept: 'application/json',
                   Authorization: auth,
               }
           });

        const data = await req.json();
        this.users = data.ResultData; 

    },

  },
  components:{
    OptionComponent,

  },
  mounted(){
    this.getAllUsers();

  },
};
</script>


<style scoped>

</style>