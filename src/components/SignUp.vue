<template>
  <form @submit.prevent="submit">
    <label for="">email</label>
    <input type="email" v-model="email" />
    <label for="">password</label>
    <input type="password" v-model="password" />
    <p v-if="pwerror" class="pwerror">{{ pwerror }}</p>
    <label for="">Role</label>
    <div>
      <select v-model="role">
        <option value="dev">Web Devloper</option>
        <option value="desinger">Web Desinger</option>
        <option value="pm">Project Manager</option>
        <option value="owner">IT company owner</option>
      </select>
    </div>
    <label for="">Skills</label>
    <div>
      <input type="text" v-model="skill" @keyup.alt="addSkill" />
    </div>
    <div v-for="skill in skills" :key="skill" class="showSkill">
      {{ skill }}
      <span class="cross" @click="deleteSkill(skill)">&#x2717;</span>
    </div>
    <!-- single checkbox -->
    <div>
      <input type="checkbox" /><span class="check"
        >Don’t have an account?
      </span>
    </div>

    <div class="aline">
      <button type="submit" class="submit">create accout</button>
    </div>

    <!-- multiple checkbox -->
    <!-- <div>
      <div>
        <input type="checkbox" v-model="names" value="koko" /><span
          class="check"
          >koko
        </span>
      </div>
      <div>
        <input type="checkbox" v-model="names" value="maymay" />
        <span class="check">maymay </span>
      </div>
      <div>
        <input type="checkbox" v-model="names" value="yuki" />
        <span class="check">yuki </span>
      </div>
      <div>
        <input type="checkbox" v-model="names" value="ayekaday" />
        <span class="check">ayekaday </span>
      </div>
      <div>
        <input type="checkbox" v-model="names" value="yukihana" />
        <span class="check">yukihana </span>
      </div>
    </div> -->
  </form>
  <p>email:{{ email }}</p>
  <p>password:{{ password }}</p>
  <p>role:{{ role }}</p>
  <p>skill:{{ skill }}</p>
  <p>skill:{{ skill }}</p>
  <p>names:{{ names }}</p>
</template>

<script>
export default {
  data() {
    return {
      email: "",
      password: "",
      role: " ",
      skill: "",
      skills: [],
      names: [],
      pwerror: "",
    };
  },
  methods: {
    addSkill(e) {
      if (e.key === "," && this.skill) {
        this.skills.push(this.skill);
        this.skill = "";
      }
    },
    deleteSkill(skill) {
      this.skills = this.skills.filter((loopSkill) => {
        return loopSkill != skill;
      });
    },
    submit() {
      const specialChar = /[!@#$%^&*(),.?":{}|<>]/;
      if (this.pwerror.length < 8 && !specialChar.test(this.password)) {
        this.pwerror =
          "Your password must be at least 8 characters and contain a special character!";
      } else alert("Form submitted successfully!");
    },
  },
};
</script>

<style>
form {
  background-color: rgb(236, 239, 241);
  width: 400px;
  height: 500px;
  margin: 30px auto;
  padding: 20px;
  text-align: left;
  border-radius: 10px;
}
label {
  margin: 20px 0 0 10px;
  display: inline-block;
  font-weight: bold;
  font-size: 12px;
  color: rgb(5, 102, 97);
  font-weight: bold;
}
input,
select {
  display: block;
  margin: 2px 0 0 10px;
  width: 100%;
  height: 30px;
  background-color: rgb(236, 239, 241);
  border: none;
  border-bottom: 1px solid rgb(202, 198, 198);

  color: steelblue;
  font-weight: bold;
}
input[type="checkbox"] {
  width: 15px;
  top: 10px;
  display: inline;
  position: relative;
}
.check {
  font-size: 15px;
  margin-left: 3px;
  color: rgb(134, 9, 26);
}
.cross {
  color: red;
  cursor: pointer;
}
.showSkill {
  margin-left: 10px;
  color: rgb(53, 35, 134);
}
.submit {
  background-color: dodgerblue;
  border-radius: 10px;
  padding: 7px;
  color: blanchedalmond;
}
.aline {
  text-align: center;
  margin-top: 15px;
}
.pwerror {
  color: red;
  font-weight: bold;
  margin-left: 10px;
}
</style>
