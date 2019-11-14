<template>
    <div class="input_info">
    
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

        <v-simple-table>
           
                <thead>
                    <tr>
                        <th class="text-left">EmployeeID</th>
                        <th class="text-left">Name</th>
                        <th class="text-left">Email</th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="employee in employeeLists" :key='employee.number'>
                        <td>{{employee.number}}</td>
                        <td>{{employee.name}}</td>
                        <td>{{employee.email}}</td>
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
export default {
    data() {

        return {
             name: "",
             email: "",
             latestNumber: 1,
             employeeLists: [
                 {number: 1, name: 'Too', email: 'too_w_o@hotmail.com'},
             ],
             ok: true,
             
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
            this.employeeLists.push({number: this.latestNumber, name: this.name, email: this.email});
            this.name = "";
            this.email = "";
        },
        doToggle() {
            this.ok = !this.ok;
        },
    },
}
</script>

<style scoped>
.input_info {
    text-align: center;
   
}
.text_field {
    background-color: sandybrown;

}
.column {
    
}
</style>