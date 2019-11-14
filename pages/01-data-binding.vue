<template>
    <div class="con-center">
        <nuxt-link to="/about">About</nuxt-link>
        <h1 v-if="ok">Hello {{name}}</h1>
        <div v-show="ok">UP NAME - {{upperName}}</div>
        <input type="text" :value="name"/>
        <input type="text" v-model="name"/>
        <v-btn @click="doSave">
            <v-icon dark>favorite</v-icon>
            Save</v-btn>
        <v-btn @click="doToggle">Toggle</v-btn>
   
        <h1>Student List</h1>
        <ul>
            <li v-for="st in student" :key="st.code"
            :class="{fail:st.score<50,good:st.score>=80}">
                <span>{{st.code}}</span>
                <span>{{st.name}}</span>
            </li>
        </ul> 

        <ul>
            <li v-for="(uname, index) in namelists" :key="index">
                {{uname}}
            </li>
        </ul> 
        
    

    </div>
</template>

<script>
export default {
    data() {
        setInterval(() => {
            this.name += "+";
        }, 5000);

        return {
             name: "",
             namelists: [],
             ok: true,
             student: [
                 {code:'001', name:'Too', score:50},
                 {code:'002', name:'Win', score:80},
                 {code:'003', name:'Boss', score:20}
             ]
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
            this.namelists.push(this.name);
            this.name = "";
        },
        doToggle() {
            this.ok = !this.ok;
        },
    },
}
</script>

<style scoped>
    .con-center {
        text-align: center;
        margin-top: 1rem;
    }
    .fail {
        color: red;
    }
    .good {
        color: green;
        font-weight: bold;
    }
</style>