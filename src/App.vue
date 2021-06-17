<template>
  <div id="app">
    <div class="container">
      <div class="card" v-for="user in users" :key="user">
        <div class="imgbox">
          <img :src="user.picture.large" alt="profile-picture" />
        </div>
        <div class="content">
          <h3>{{ user.name.first }} {{ user.name.last }}</h3>
          <p>
            Nationality : {{ user.location.country }}
                <br />
                Phone :
                {{ user.phone }}
                <br />
                Mobile :
                {{ user.cell }}
                <br />
                Email address :
                <br>
                {{ user.email }}
          </p>
        </div>
      </div>

    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "App",
  data() {
    return {
      users: "",
    };
  },
  created() {
    axios
      .get("https://randomuser.me/api/?results=20")
      .then((response) => (this.users = response.data.results));
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  font-family: "montserrat", sans-serif;
}

#app {
  display: flex;
  justify-content: center;
  align-items: center;
  background-image: url(./images/bg1.jpg);
  background-size: cover;
  height: 100%;
}
.container {
  position: relative;
  width: 1100px;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
  padding: 30px;
}
.container .card {
  position: relative;
  max-width: 300px;
  height: 215px;
  background: #fff;
  margin: 30px 10px;
  padding: 20px 15px;
  display: flex;
  flex-direction: column;
  box-shadow: 0 5px 202px rgba(0, 0, 0, 0.5);
  transition: 0.3 ease-in-out;
  border-radius: 10px;
}
.container .card:hover {
  height: 325px;
}
.container .card .imgbox {
  position: relative;
  width: 250px;
  height: 250px;
  top: -60px;
  z-index: 1;
  box-shadow: 0 5px 20px rgba(0, 0, 0, 0.2);
  border-radius: 150px;
}
.container .card .imgbox img {
  max-width: 100%;
  margin: 0 auto;
  width: 100%;
  height: 100%;
  border-radius: 150px;
}
.container .card .content h3{
  font-size: 18px;
}
.container .card .content {
  font-size: 12px;
  max-width: 220px;
  position: relative;
  margin-top: -140px;
  padding: 10px 15px;
  text-align: center;
  color: #111;
  visibility: hidden;
  opacity: 0;
  transition: 0.3s ease-in-out;

}

.container .card:hover .content {
  visibility: visible;
  opacity: 1;
  margin-top: -40px;
  transition-delay: 0.2s;
}
</style>
