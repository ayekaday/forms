<template>
  <form>
    <label for="">Email</label>
    <input type="email" required v-model="email" />
    <label for="">Password</label>
    <input type="password" required v-model="password" />
    <label for="">Role</label>
    <select v-model="role">
      <option value="dev">Web developer</option>
      <option value="ui">Web desinger</option>
      <option value="pm">Project Manager</option>
    </select>

    <div>
      <label for="">skills</label>
      <input type="text" v-model="skill" @keyup.alt="addSkill" />
    </div>

    <div v-for="skill in skills" :key="skill">
      {{ skill }}
    </div>
    <!-- single checkbox -->
    <div>
      <input type="checkbox" v-model="accept" />
      <label for="">Accept terms and conditions</label>
    </div>
  </form>
</template>

<script>
export default {
  data() {
    return {
      email: "@gmail.com",
      password: "",
      role: "",
      accept: false,
      skill: "",
      skills: [],
    };
  },
  methods: {
    addSkill(e) {
      if (e.key === ",") {
        this.skills.push(this.skill);
        this.skill = "";
      }
    },
  },
};
</script>

<style>
form {
  background-color: rgb(245, 243, 243);
  width: 350px;
  height: 400px;
  padding: 40px;
  margin: 30px;
  text-align: left;
  border-radius: 10px;
  margin: 30px auto;
}
label {
  color: cadetblue;
  display: inline-block;
  font-size: 11px;
  margin: 10px 0 0;
  font-weight: bold;
  text-transform: uppercase;
}
input,
select {
  display: block;
  margin: 5px 0 15px;
  width: 100%;
  height: 30px;
  color: rgb(22, 21, 1);
  border: none;
  background-color: rgb(245, 243, 243);
  border-bottom: 1px solid grey;
}
input[type="checkbox"] {
  display: inline-block;
  width: 10px;
  position: relative;
  margin-right: 10px;
  top: 10px;
}
</style>
