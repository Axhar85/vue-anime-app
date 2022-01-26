<template>
  <div class="app">
    
    <header>
      <h1>The<strong>Anime</strong>Database</h1>
      <form class="search-box">
      <input type="search" class="search-field" placeholder="Search the anime .... " >
    </form>
    </header>
    <body>
      <div class="card">
        <Card />
      </div>
    </body>
    
  </div>
</template>

<script>
import Card from './components/Card';

export default {
  setup(){
    return(
      Card
    )
  }

}
</script>

<style >
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
  font-weight: bold;
}
a {
  text-decoration: none;
}
header {
  padding-top: 50px;
  padding-bottom: 50px;

}


  h1{
    color: #888;
    text-align: center;
    font-size: 42px;
    font-weight: 400;
    text-transform: uppercase;
    margin-bottom: 30px;


  }
  h1:hover{
    color: #313131;
  }
    strong {
      color: #313131;
    }

  .search-box {
    display: flex;
    justify-content: center;
    padding-left: 30px;
    padding-right: 30px;

  }
  .search-field {
      appearance: none;
      background: none;
      border: none;
      outline: none;
      background-color: #f3f3f3;
      box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.15);
      display: block;
      width: 100%;
      max-width: 600px;
      padding: 15px;
      border-radius: 8px;

      color: #313131;
      font-size: 20px;

    }

  main {
    max-width: 1200px;
    margin: 0 auto;
    padding-left: 30px;
    padding-right: 30px;
    }
    .cards {
      display: flex;
      flex-wrap: wrap;
      margin: 0 -8px;
    }
    
</style>
