<template>
    <div class="text_field">
    
        <v-row>    
                <v-col cols="12" sm="6" md="2" offset-md="5"
                class="column" 
                :align-self="center">
                <v-text-field
                    v-model="name"
                    label="Product name"
                    placeholder="Fill in the blank"
                ></v-text-field>
                </v-col>
                <v-col cols="12" sm="6" md="2" offset-md="5"
                class="column" 
                :align-self="center">
                <v-text-field
                    v-model="description"
                    label="Description"
                    placeholder="Fill in the blank"
                ></v-text-field>
                </v-col>
                <v-col cols="12" sm="6" md="2" offset-md="5"
                class="column" 
                :align-self="center">
                <v-text-field
                    v-model="price"
                    label="Price"
                    placeholder="Fill in the blank"
                ></v-text-field>
                </v-col>
                <v-col cols="12" sm="6" md="2" offset-md="5"
                class="column" 
                :align-self="center">
                <v-text-field
                    v-model="branchID"
                    label="branchID"
                    placeholder="Fill in the blank"
                ></v-text-field>
                </v-col>
                
        </v-row>
        
        <v-btn @click="doAdd">
            <v-icon dark>favorite</v-icon>Add
        </v-btn>
        <v-btn @click="doToggle">
            <v-icon dark>event</v-icon> Display Table
        </v-btn>

        <v-simple-table v-show="displayTable">
           
                <thead>
                    <tr>
                        <th class="text-left">ProductID</th>
                        <th class="text-left">Product Name</th>
                        <th class="text-left">Description</th>
                        <th class="text-left">Price</th>
                        <th class="text-left">BranchID</th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="product in products" :key='product.number'>
                        <td>{{product.number}}</td>
                        <td>{{product.name}}</td>
                        <td>{{product.description}}</td>
                        <td>{{product.price}}</td>
                        <td>{{product.branchID}}</td>
                        <v-btn @click.prevent="deleteProduct(product.number)">Delete</v-btn>
                    </tr>
                </tbody>
        
        </v-simple-table>        
    </div>
        

    
</template>
<script>

export default {
    name: 'member_search',
    data() {

        return {
             name: "",
             description: "",
             price: "",
             branchID: "",
             latestNumber: 1,
             products: [
                 {number: 1, name: 'Condom', description: 'safety',price:'80',branchID:'112'},
             ],
             displayTable: true,
             
        }
    },
    watch: {
        namelists() {
            if (this.namelists.length > 20) {
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
        doAdd() {
            console.log('ADD');
            this.latestNumber += 1;
            this.products.push({number: this.latestNumber, name: this.name, description: this.description, price: this.price,branchID: this.branchID});
            this.name = "";
            this.description = "";
            this.price = "";
            this.branchID = "";
        },
        doToggle() {
            this.displayTable = !this.displayTable;
        },
        deleteProduct(number) {
            this.products = this.products.filter(
                product => product.number !== number
            )
        },
        editProduct(number, updatedProduct) {
            this.product = this.product.map(product => 
            product.number === number ? updatedProduct : product)
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