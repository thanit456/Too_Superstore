<template>
    <div class="input_info">
           
        <v-row>
            <v-col cols="50" sm="6" md="5">
                <v-text-field class="text_field" type="text" v-model="name"
                label="Username" placeholder="Fill in the blank"></v-text-field> 
                <v-text-field class="text_field" type="text" v-model="email"
                label="Email" placeholder="Fill in the blank"></v-text-field> 
            </v-col>
        </v-row>
        
        <v-btn @click="doSave">
            <v-icon dark>favorite</v-icon>Save
        </v-btn>

        <!-- <div>
            <ul>
                <li v-for="(employee, index) in employeeLists" :key='index'>
                    <span>{{employee.number}}</span>    
                    <hr>
                    <span>{{employee.name}}</span>    
                    <hr>
                    <span>{{employee.email}}</span>    
                    <hr>


                </li>
            </ul>
        </div> -->

        <v-data-table
        ::headers="headers"
        ::items="employeeLists"
        ></v-data-table>
        

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
             headers: [
                 {
                    text: 'Employee number',
                    align: 'left',
                    sortable: false,
                    width: '100px',
                    value: 'number'
                 },
                 {
                     text: 'Name',
                     value: 'name',
                     width: '100px',
                 },
                 {
                    text: 'Email',
                    value: 'email',
                    width: '100px',
                 }
             ],
             width: '200px',

             
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
</style>