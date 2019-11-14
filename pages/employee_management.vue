<template>
    <div class="input_info">
        <v-text-field type="text" v-model="name"/> 
        <v-text-field type="text" v-model="email"/> 
        
        <v-btn class='text_field' @click="doSave">
            <v-icon dark>favorite</v-icon>Save
        </v-btn>

        <div>
            <ul>
                <li v-for="(employee, index) in employeeLists" :key='index'>
                    <span>{{employee.name}}</span>    
                    <span>{{employee.email}}</span>    

                </li>
            </ul>
        </div>

    </div>
</template>
<script>
export default {
    data() {

        return {
             name: "",
             email: "",
             employeeLists: [
                 {name: 'Too', email: 'too_w_o@hotmail.com'},
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
            this.employeeLists.push({name: this.name, email: this.email});
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