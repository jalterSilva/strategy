<template>
 
<nav class="navbar navbar-expand-lg navbar-light" style="background-color: #f2f2f2;">
  <div class="container-fluid">
    <router-link to="/" id="logo-url"><img :src="logo" :alt="alt" id="logo"> </router-link>
    <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse justify-content-center" id="navbarNav">
      <ul class="navbar-nav">
        <li class="nav-item">
            <a class="nav-link">
                <router-link to="/">Home</router-link>
            </a>
        </li>

        <li class="nav-item">
          <a class="nav-link">
            <router-link to="/users">Users</router-link>
         </a>
        </li>  

      </ul>

    </div>
  </div>
</nav>
     

</template>

<script>
export default{
     name: "NavBar",
     props: ["logo", "alt"]
}
</script>

<style scoped>

#nav{
    background-color: #153d77;
    border-bottom: 4px solid #153d77;
    padding: 15px 50px;
    display: flex;
    justify-content: center;
    align-items: center;
}

#nav #logo-url{
    margin:0 auto;
    margin-left:0;
}

#logo{
    width: 140px;
    height: 80;

}

#nav a{
    color: #d9d9d9;
    text-decoration: none;
    margin: 12px;
    transition: .3s;
}

#nav a:hover{
    color: white;
}

</style>
