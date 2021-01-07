<template>
  <div id="app">
  
    <main>
      <div class="search-box">
        <input type="text" class="search-bar" placeholder="Search for a country..." v-model="query" v-on:input="fetchCountry" /> 
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
        
    <div class="main-content">
      <!--<div class="home-country-box" v-if="typeof country != 'undefined'">-->
      <div class="home-country-box" v-for="c in filteredCountry" :key="c.countrydetail">
        <div class="home-country-flag">
         <img v-bind:src="c.flag" />
        </div>

        <div class="home-country-details">
          <div class="home-country-name" style="font-weight:800; font-size: 14px; margin: 0 0 10px 0;">
          {{ c.name }}
          </div>

        <div class="home-country-title">Population:</div>
          <div class="home-country-population">
            {{ Number(c.population).toLocaleString() }}
            <br/>
          </div>

        <div class="home-country-title">Region:</div>
          <div class="home-country-region">
              {{ c.region }}  
            <br/>
          </div>

        <div class="home-country-title">Capital:</div>
          <div class="home-country-capital">
            {{ c.capital }}
            <br/>
          </div>
        </div>
        
      </div>
    </div>

  </div>
</template>

<script>

export default {
  name: 'app',
  data () {
    return {
      url_base: 'https://restcountries.eu/rest/v2/',
      query: '',
      country: {}
    }
  },
  methods:{

    // fetchCountry(){
    //   //fetch('${this.url_base}name/?q=${this.query}')
    //   //fetch('${this.url_base}') // Error
    //   //fetch('https://restcountries.eu/rest/v2/name/${this.query}')
    //   //fetch('https://restcountries.eu/rest/v2/name/afg') // <--- This format 'afg' is query.
    //   fetch('https://restcountries.eu/rest/v2/') // <--- This format is to print all country into array. '..v2/name' is ERROR!
    //   //fetch('https://restcountries.eu/rest/v2/$(this.query}')
    //     .then(res => {
    //       return res.json();
    //     }).then(this.setResults);
    // },
    // setResults(results){
    //   this.country = results;
    //  console.log(results);
    // }
  
    // },
  //Lifecycle Hooks - To show all countries when loaded
  mounted(){
    fetch('https://restcountries.eu/rest/v2/')
      .then(res => {
        return res.json();
      }).then(this.setResults);
    setResults(results);{
      this.country=results;
      console.log(results);
    }
  },
  computed:{
    filteredCountry: function(){
      return this.country.filter((c) => {
        return c.title.match(this.query);
      });
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
    min-height: 15vh;
    max-width: 1440px;
    padding: 30px 50px;
    overflow-wrap: break-word;
    transition: 0.4s;
  }

  .main-content {
    min-height: 95vh;
    max-width: 1440px;
    padding: 30px 50px;
    overflow-wrap: break-word;
    transition: 0.4s;
    
    color: hsl(0, 0%, 100%);
    font-size: 14px;
  }

  .home-country-box {
    display: inline-block;
    max-width: 240px;
    height: auto;
    margin: 30px 47px;
    background-color: hsl(209, 23%, 22%);
  }

  .home-country-flag {
    padding: 0;
  }

  .home-country-flag img {
    width: 240px;
    height: 160px;
  }

  .home-country-details {
    padding: 15px 15px 35px 15px;
  }

  .home-country-title, .home-country-population, .home-country-region, .home-country-capital {
    display: inline;
  }

  .home-country-title{
    font-weight:600; 
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

  .dropbox-content {
    display: none;
    background-color: hsl(209, 23%, 22%);
    min-width: 160px;
    z-index: 1;
  }

  .dropbox-content a {
    color: hsl(0, 0%, 100%);
    background-color: hsl(209, 23%, 22%);
    padding: 12px 16px;
    text-decoration: none;
    display: block;
  }

  .dropbox-content a:hover {
    background-color: hsl(209, 23%, 25%);
  }

  .drop-box:hover .dropbox-content {
    margin: 50px 0 0 0;
    display: block;
    position: absolute;
  }

</style>
