<template>
  <div id="app">

    <div class="top-bar">
      <div id="title">
        Where in the world?
      </div>
      <div id="mode" href="#">
        <div id="moon-icon">
          <i class="far fa-moon"></i>
        </div>
        <div id="mode-word"></div>
          Dark Mode
      </div>
    </div>

    <main>
      <div class="search-box">
        <input type="text" class="search-bar" placeholder="Search for a country..." />
        <button type="submit"><i class="fas fa-search"></i></button> 
      </div>

      <div class="drop-box">
        <div id="down-icon">
          <i class="fas fa-caret-down"></i>
        </div>
        <button class="drop-button">Filter by Region</button>
        <div class="dropbox-content">
          <a href="#">Africa</a>
          <a href="#">America</a>
          <a href="#">Asia</a>
          <a href="#">Europe</a>
          <a href="#">Ocenia</a>
        </div>
      </div>
      
    </main>

  </div>
</template>

<script>

export default {
  name: 'App',
  data () {
    return {
      url_base: 'https://restcountries.eu/rest/v2/all'
    }
  }

}
</script>

<style>

  @font-face {
    font-family: 'Nunito Sans';
    font-style: normal;
    font-weight: 300;
    src: url(https://fonts.gstatic.com/s/nunitosans/v6/pe0qMImSLYBIv1o4X1M8cce9I9s.woff2) format('woff2');
    unicode-range: U+0000-00FF, U+0131, U+0152-0153, U+02BB-02BC, U+02C6, U+02DA, U+02DC, U+2000-206F, U+2074, U+20AC, U+2122, U+2191, U+2193, U+2212, U+2215, U+FEFF, U+FFFD;
  }

  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: Nunito Sans;
    font-weight: 300;
  }

  #app {
    background-color: hsl(207, 26%, 17%);
  }

  main {
    min-height: 100vh;
    max-width: 1440px;
    padding: 30px 50px;
    overflow-wrap: break-word;
    transition: 0.4s;
  }

  .search-box {
    width: 30%;
    margin-bottom: 30px;
    float: left;
  }

  .search-box .search-bar {
    width: 80%;
    padding: 17px;
    color: hsl(0, 0%, 100%);
    font-size: 14px;
    appearance: none;
    border: none;
    outline: none;
    background: none;
    background-color: hsl(209, 23%, 22%);
    border-radius: 0px 5px 5px 0px;
    transition: 0.4s;
    float: right;
  }

  .search-box .search-bar:focus {
    background-color: hsl(209, 23%, 25%);
  }

  ::placeholder {
    color: hsl(0, 0%, 100%);
  }

  .search-box button {
  float: left;
  width: 20%;
  padding: 15px;
  background-color: hsl(209, 23%, 22%);
  color: white;
  border: none;
  cursor: pointer;
  border-radius: 5px 0px 0px 5px;
  }

  .search-box:after {
    content: "";
    clear: both;
    display: table;
  }

  .drop-box{
  float: right;
  width: 15%;
  }

  #down-icon i{
    color: white;
    width: 20%;
    height: auto;
    overflow: hidden;
    margin-bottom: 5px;
    background-color: hsl(209, 23%, 22%);
    color: white;
    float: right;
    padding: 17.5px;
    margin-left: 0;
    border-radius: 0px 5px 5px 0;
  }

  .drop-button{
    background-color: hsl(209, 23%, 22%);
    color: hsl(0, 0%, 100%);
    padding: 15px;
    font-size: 14px;
    border: none;
    cursor: pointer;
    border-radius: 5px 0 0 5px;
    margin-bottom: 5px;
    width: 80%;
    text-align: left;
    float: left;
  }

  .dropbox-content{
    display: none;
    background-color: hsl(209, 23%, 22%);
    min-width: 160px;
    z-index: 1;
  }

  .dropbox-content a{
    color: hsl(0, 0%, 100%);
    background-color: hsl(209, 23%, 22%);
    padding: 12px 16px;
    text-decoration: none;
    display: block;
  }

  .dropbox-content a:hover{
    background-color: hsl(209, 23%, 25%);
  }

  .drop-box:hover .dropbox-content {
    display: block;
  }

  .top-bar{
    padding: 15px 50px;
    border: hidden;
    background-color: hsl(209, 23%, 22%);
    margin: auto;
    overflow: hidden;
    transition: 0.4;
  }

  .top-bar #title {
    color: hsl(0, 0%, 100%);
    width: 13%;
    float: left;
    font-weight: 800;
    font-size: 16px;
    padding: 5px;
  }

  .top-bar #mode {
    color: hsl(0, 0%, 100%);
    float: right;
    font-weight: 600;
    font-size: 14px;
    width: 8%;
    text-align: right;
    padding: 5px;
  }

  #moon-icon {
    padding: 0px;
    color: white;
    width: 16px;
    height: auto;
    float: left;
    overflow: hidden;
  }


  #mode-word {
    float: right;
  }

</style>
