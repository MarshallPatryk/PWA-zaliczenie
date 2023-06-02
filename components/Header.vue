<template>
    <header>
      <nav>
        <div class="logo">Zaliczę?</div>
        <div class="toggle" @click="isOpen = !isOpen">
          <img src="https://cdn-icons-png.flaticon.com/512/1828/1828778.png"/>
        </div>
        <ul :class="{ 'is-open': isOpen }">
          <li><NuxtLink to="/">Strona Główna</NuxtLink></li>
          <li><NuxtLink to="/about">Galeria</NuxtLink></li>
          <li><a href="/photos/">Parametry</a></li>
          <li><a href="/nasa/">Dane Axios</a></li>
          <li><a href="/nasaBezAxios/">Dane Fetch</a></li>
          <li><a href="/nasaGallery/">Galeria NASA</a></li>
        </ul>
      </nav>
    </header>
  </template>
  
  <script>
  export default {
    data() {
      return {
        isOpen: false,
      };
    },
  };
  </script>
  
  <style scoped>
  header {
    background-color: #4F345A;
    padding: 20px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    border-bottom: 4px solid #C9F299;
  }
  
  nav {
    display: flex;
    justify-content: space-between;
    align-items: center;
    flex-wrap: wrap;
  }
  
  .logo {
    font-size: 1.8rem;
    font-weight: bold;
    text-decoration: none;
    color: #C9F299;
  }
  
  .toggle {
    cursor: pointer;
  }
  
  @media (max-width: 768px) {
    .toggle {
      display: flex;
      flex-direction: column;
      justify-content: space-between;
      width: 20px;
      height: 20px;
    }
  
    ul {
      display: none;
      position: absolute;
      top: 68px;
      left: 0;
      background-color: #4F345A;
      width: 100%;
      padding: 10px;
      box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
      z-index: 1;
      list-style-type: none;
    }
  
    ul.is-open {
      display: block;
    }
  
    ul li {
      margin: 10px 0;
    }
  }
  
  @media (min-width: 769px) {
    .toggle {
      display: none;
    }
  
    nav ul {
      display: flex;
      justify-content: flex-end;
      align-items: center;
    }
  
    nav ul li {
      margin: 0 40px;
      display: inline-block;
    }
  }
  </style>
  