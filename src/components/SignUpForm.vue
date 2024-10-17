<template>
  <form @submit.prevent="handleSubmit">
    <lablel>
        Email
    </lablel>
    <input type="email" required v-model="email">
    <lablel>
        Password
    </lablel>
    <input type="Password" required v-model="password">
    <div v-if="passwordError" class="error">{{passwordError}}</div>
    <label>
        Role 
    </label>
    <select v-model="role">
        <option value="developer">Web Developer</option>
        <option value="designer">Web Designer</option>
    </select>
    <label> skills:</label>
    <input type="text" v-model="tempSkill" @keyup.alt="addSkill" required />
    <div class="terms">
        <input type="checkbox" id="terms" v-model="terms" required>
        <label>Accept the terms and policy</label>
    </div>
    <div>
        <input type="checkbox" value="Biruk" v-model="names"/>
        <label>Biruk</label>
    </div>
    <div>
        <input type="checkbox" value= "Getachew" v-model="names"/>
        <label>Getachew</label>
    </div>
    <div>
        <input type="checkbox" value="reggasa" v-model="names"/>
        <label>Reggasa</label>
    </div>
    <button>create Acount</button>
  </form>
  <p>Email :{{email}}</p>
  <p>Password :{{password}}</p>
  <p>Role :{{role}}</p>
  <p>Terms :{{terms}}</p>
  <p>Names :{{names}}</p>
  <p>Skills :{{tempSkill}}</p>
  <div v-for="skill in skills" :key="skill" class="pill">
<span @click="deleteSkill(skill)">{{ skill }}</span>  
  </div>
</template>

<script>
export default {
 data (){
    return{
        email:'',
        password:'',
        role:"designer",
        terms:false,
        names:[],
        tempSkill:'',
        skills:[],
        passwordError:''

    }
 },
 methods :{
    addSkill(e){
      if(e.key === ',' && this.tempSkill){
        if(this.skills.includes(this.tempSkill)){
            alert('you have already added this skill')
        }else{
        this.skills.push(this.tempSkill)
        this.tempSkill = ''
        }
      }
    },
    deleteSkill (skill){
this.skills = this.skills.filter((item)=>{
    return skill !== item
})
    },
    handleSubmit (){
//validate password
  this.passwordError = this.password.length > 5 ? '' : "the Password is at least 5 chars"
  if(!this.passwordError){
    console.log("formed data")
  }
    }
 }
}
</script>

<style>

</style>