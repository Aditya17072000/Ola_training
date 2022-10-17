<template>
<div>{{greet}} {{name}}</div>
<div v-html="number"></div>
<div v-html="hack"></div>
<h1 :id="headingID">head</h1>
<button :disabled="button">press</button>
<h2 class="underline">Underline</h2>
<h2 class="underline" :class="status">status</h2>
<h2 :class="Ispromoted && 'promotion'">promoted</h2>
<h2 :class="soldOut? 'sold':'notsold'">sold</h2>
<h2 :class="soldout || 'sold'">boom</h2>
<h2 :class="[soldout && 'sold',soldOut? 'sold':'notsold']">Newly released movie</h2>
<h2 :class="{
  promotion:Ispromoted,
  notsold:!soldOut,
  'sold':soldOut
}">Object example</h2>
<h2 :style="headerStyle">object style</h2>
<div :style="[passStyle,dangerStyle]">array style</div>

<h2 v-if="num>0">the number is positive</h2>
<h2 v-else-if="num<0">the number is negative</h2>
<h2 v-else-if="num==0">the number is zero</h2>
<h2 v-else>not a number</h2>
<template v-if="display">
    <h2>Aditya</h2>
    <h2>vue</h2>
    <h2>rfadrfser</h2>
</template>
<h2 v-show="showCheck">check v-show</h2>
<h2 v-if="showCheck">chech v-if</h2>
<h2 v-for="(name,index) in names" :key="name">{{ index +1}} {{ name }}</h2>
<h2 v-for="name in fullNames" :key="name.first">{{name.first}} {{name.last}}</h2>
<div v-for="actor in actors" :key="actor.firstName">
    <h2>{{actor.firstName}}</h2>
    <h3 v-for="movie in actor.movies" :key="movie">{{movie}}</h3>
</div>
<h2 v-for="value,index,key in myInfo" :key="value">{{key}} {{index}} {{value}}</h2>
<template v-for="name in names" :key="name">
    <h2>{{name}}</h2>
    <hr />
</template>
<template v-for="name in names" :key="name">
    <h2 v-if="name=='mark'">{{name}}</h2>
</template>
<h2>{{add(10,234)}}</h2>
<h2>{{multiply(20)}}</h2>

<h2>{{name}}</h2>
<div>
    <button v-on:click="changeName($event),increment($event)">change name</button>
</div>
<h2>{{count}}</h2>
<div>
    <button @click="increment(1)">Increment</button>
    <button @click="decrement(1)">Decrement</button>
</div>
<div>
  <pre>
    {{JSON.stringify(formValue,null,2)}}
    <!-- {{JSON.stringify(profileSumm,null,2)}} -->
  </pre>
</div>
<form @submit="submitForm">
  <div>
    <label for="name">Name</label>
    <input type="text" id="name" v-model="formValue.name">
  </div>
  <div>
    <label for="profile">Profile Summary</label>
    <textarea id="profile" v-model="formValue.profileSum" />
  </div>
  <div>
    <label for="country">Country</label>
    <select id="country" v-model="formValue.country">
    <option value="">Select a country</option>
    <option value="india">India</option>
    <option value="usa">USA</option>
    <option value="england">England</option>
    </select>
  </div>
  <div>
    <label for="job-location">Job location</label>
    <select id="job-location" multiple v-model="formValue.jobLocation">
    <!-- <option value="">Select a country</option> -->
    <option value="india">India</option>
    <option value="usa">USA</option>
    <option value="england">England</option>
    </select>
  </div>
  <div>
    <input type="checkbox" id="remotework" v-model="formValue.remoteWork" true-value="yes" false-value="no">
    <label for="remotework">Opting for remote work</label>
  </div>
  <div>
    <label>skills you know</label>
    <input type="checkbox" id="html" value="HTML" v-model="formValue.skillSet">
    <label for="html">HTML</label>
    <input type="checkbox" id="css" value="CSS" v-model="formValue.skillSet ">
    <label for="css">CSS</label>
    <input type="checkbox" id="javascript" value="Javascript" v-model="formValue.skillSet">
    <label for="javascript">Javascript</label>
  </div>
  <div>
    <label>Years of Experience</label>
    <input type="radio" id="0-2" value="0-2" v-model="formValue.yearExp">
    <label for="0-2">0-2</label>
    <input type="radio" id="3-5" value="3-5" v-model="formValue.yearExp">
    <label for="3-5">3-5</label>
    <input type="radio" id="6-10" value="6-10" v-model="formValue.yearExp">
    <label for="6-10">6-10</label>
    <input type="radio" id="10+" value="10+" v-model="formValue.yearExp">
    <label for="10+">10+</label>
  </div>
  <div>
    <button>Submit</button>
  </div>
</form>
</template>

<script>
// import { METHODS } from 'http';

// import { isInDestructureAssignment } from '@vue/compiler-core';

// import { isInDestructureAssignment } from '@vue/compiler-core';

export default {
    name: 'App',
    data() {
        return {
            formValue:{
              name:'',
              profileSum:'',
              country:'',
              jobLocation:[],
              remoteWork:'no',
              skillSet:[],
              yearExp:''
            },
            
            greet: 'Hello',
            name: 'Aditya',
            number: '<b>2342342344</b>',
            hack: '<a href="#">win a prize</a>',
            headingID: 'heading',
            button: true,
            status: 'danger',
            Ispromoted: true,
            soldOut: false,
            headerStyle: {
                color: 'orange',
                fontSize: '50px'
            },
            passStyle: {
                color: 'blue',
                backgroundColor: 'lightgreen',
                border: '1px solid green'
            },
            dangerStyle: {
                padding: '20px',
                fontStyle: 'Italics',
                fontSize: '50px'

            },
            num: 4,
            display: false,
            showCheck: false,
            names: ['bruce', 'mark', 'dienna'],
            fullNames: [{
                    first: 'Bruce',
                    last: 'Banner'
                },
                {
                    first: 'Mark',
                    last: 'Ruffalo'
                },
                {
                    first: 'Princess',
                    last: 'Dienna'
                }
            ],
            actors: [{
                    firstName: 'caprio',
                    movies: ['Inception', 'Titanic']
                },
                {
                    firstName: 'Evans',
                    movies: ['captain America', 'avengers']
                }
            ],
            myInfo: {
                name: 'Aditya',
                company: 'Ola',
                course: 'Vue'
            },
            multiplier: 4,
            count: 0
        };
    },
    methods: {
        submitForm(event){
          event.preventDefault()
          console.log(this.formValue)
        },
        add(a, b) {
            return a + b
        },
        multiply(num) {
            return num * this.multiplier
        },
        changeName(event) {
            this.name = 'batman'
            console.log(event)
        },
        increment(event) {
            this.count += 1
            console.log(event)
        },
        decrement(event) {
            this.count -= 1
            console.log(event)
        }
    }
}
</script>

<style>
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    /* text-align: center; */
    color: #2c3e50;
    margin-top: 60px;
}

label {
    font-weight: bold;
    display: flex;
    margin-bottom: 6px;
}

input+label {
    font-weight: bold;
    display: inline-flex;
    margin-right: 20px;
}

.underline {
    text-decoration: underline;
}

.promotion {
    font-style: italic;
}

.sold {
    color: red
}

.notsold {
    color: green
}
</style>
