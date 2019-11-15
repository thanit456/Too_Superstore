<template>
    <div>
       <HelloWorld />
    </div>
</template>

<script>
import HelloWorld from '../components/HelloWorld.vue'

export default {
    name: 'form_employee',
    components: [
        HelloWorld
    ],
    data() {
        return {
            name: "Thanit",
            employees: [
                {
                id: 1,
                name: "Richard Hendricks",
                email: 'richard@piedpiper.com',
                }, 
                {
                id: 2,
                name: 'Bertram Gilfoyle',
                email: 'gilfoyle@piedpiper.com',
                },
                {
                id: 3,
                name: 'Dinesh Chugtai',
                email: 'dinesh@piedpiper.com',
                }
            ]
        }
    },
    methods: {
        addEmployee(employee) {
            const lastId = 
                this.employees.length > 0
                ? this.employees[this.employees.length - 1].id
                : 0
            const id = lastId + 1
            const newEmployee = {...employee, id}
            this.employees = [...this.employees, newEmployee]
        },
    },
}
</script>

<style scoped>
</style>