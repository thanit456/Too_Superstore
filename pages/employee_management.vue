<template>
    <div class="text_field">
    
        <v-row>    
                <v-col cols="12" sm="6" md="2" offset-md="5"
                class="column" 
                :align-self="center">
                <v-text-field
                    v-model="name"
                    label="Username"
                    placeholder="Fill in the blank"
                ></v-text-field>
                </v-col>
                <v-col cols="12" sm="6" md="2" offset-md="5"
                class="column">
                <v-text-field
                    v-model="email"
                    label="Email"
                    placeholder="Fill in the blank"
                ></v-text-field>
                </v-col>
        </v-row>
        
        <v-btn @click="doSave">
            <v-icon dark>favorite</v-icon>Save
        </v-btn>
        <v-btn @click="doToggle">
            <v-icon dark>event</v-icon> Display Table
        </v-btn>

        <v-simple-table v-show="displayTable">
           
                <thead>
                    <tr>
                        <th class="text-left">EmployeeID</th>
                        <th class="text-left">Name</th>
                        <th class="text-left">Email</th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="employee in employees" :key='employee.number'>
                        <td>{{employee.number}}</td>
                        <td>{{employee.name}}</td>
                        <td>{{employee.email}}</td>
                        <!-- <v-btn @click="editEployee">Edit</v-btn> -->
                        <v-btn @click="deleteEmployee(employee.number)">Delete</v-btn>
                    </tr>
                </tbody>
        
        </v-simple-table>
    
        <!-- <div>
            <ul>
                <li v-for="(employee, index) in employeeLists" :key='index'>
                    <span>{{employee.number}}</span>    
                    
                    <span>{{employee.name}}</span>    
                    
                    <span>{{employee.email}}</span>    
                    

                </li>
            </ul>
        </div> -->

        <!-- <v-data-table
        ::headers="headers"
        ::items="employeeLists"
        ></v-data-table> -->
   
   
   
    </div>
        

    
</template>
<script>

import EmployeeTable from '../components/EmployeeTable.vue'
import EmployeeForm from '../components/EmployeeForm.vue'

export default {
    name: 'employee_mangement',
    component: [
        EmployeeTable,
        EmployeeForm,
    ],
    data() {

        return {
             name: "",
             email: "",
             latestNumber: 1,
             employees: [
                 {number: 1, name: 'Too', email: 'too_w_o@hotmail.com'},
             ],
             displayTable: true,
             
        }
    },
    watch: {
        namelists() {
            if (this.namelists.length > 4) {
                alert("Length: " + this.namelists.length);
            }
        }
    },
    computed: {
            upperName() { 
                return this.name.toUpperCase()
            }
    },
    methods: {
        doSave() {
            console.log('SAVE');
            this.latestNumber += 1;
            this.employees.push({number: this.latestNumber, name: this.name, email: this.email});
            this.name = "";
            this.email = "";
        },
        doToggle() {
            this.displayTable = !this.displayTable;
        },
        deleteEmployee(number) {
            this.employees = this.employees.filter(
                employee => employee.number !== number
            )
        },
        editEployee(number, updatedEmployee) {
            this.employee = this.employee.map(employee => 
            employee.number === number ? updatedEmployee : employee)
        }
    },
}
</script>

<style scoped>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}

.text_field {
    background-color: sandybrown;

}
.small-container {
  max-width: 680px;
}
</style>