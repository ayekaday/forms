<template>
  <form>
    <label for="">Email</label>
    <input type="email" required />
    <label for="">Password</label>
    <input type="password" required />
  </form>
</template>

<script>
export default {};
</script>

<style>
form {
  background-color: rgb(245, 243, 243);
  width: 300px;
  height: 200px;
  padding: 30px;
  margin: 30px;
  text-align: left;
}
label {
  color: cadetblue;
  display: inline-block;
  font-size: 15px;
  margin: 20px 0 0;
}
input {
  display: block;
  margin: 5px 0 15px;
  width: 100%;
  height: 30px;
  color: rgb(22, 21, 1);
  border: none;
  background-color: rgb(245, 243, 243);
  border-bottom: 1px solid grey;
}
</style>
