<template>

    <div class="top-bar">
      <router-link to="/">
        <div id="title">
          Where in the world?
        </div>
      </router-link>
      <a id="mode" href="#">
        <div id="moon-icon">
          <i class="far fa-moon"></i>
        </div>
        <div id="mode-word"></div>
          Dark Mode
      </a>

  <router-view/>

    </div>

</template>


    <style>
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

        #mode {
        text-decoration: none;
        }

        #mode-word {
        float: right;
        }

    </style>