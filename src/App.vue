<template>
  <div id="nav">
    <router-link to="/">Home</router-link> |
    <router-link to="/about">About</router-link>
  </div>
  <router-view/>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}

.box {
  background-color: cornflowerblue;
  color: #fff;
  padding: 20px;
  border-radius: 20px;
  margin-bottom: 10px;
}

.box1 {
  background-color: cornflowerblue;
}

.box2 {
  background-color: black;
}

.box3 {
  background-color: orange;
}

.parent {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-template-rows: repeat(3, 1fr);
  grid-column-gap: 20px;
  grid-row-gap: 20px;
}

.parent .parent-child{
  background: #e0e0e0;
  transition: 0.5s;
  padding: 5px;
  background-color: #fff;
  -webkit-border-radius: 20px;
  -webkit-border-bottom-right-radius: 100px;
  -moz-border-radius: 20px;
  -moz-border-radius-bottomright: 100px;
  border-radius: 20px;
  border-bottom-right-radius: 100px;
  -webkit-box-shadow: 5px 5px 15px 5px rgba(0,0,0,0.5); 
  box-shadow: 5px 5px 15px 5px rgba(0,0,0,0.5);
}

.parent-child-internal {
  padding: 20px;
  color:#fff;
  background-color: #333;
  -webkit-border-radius: 20px;
  -webkit-border-bottom-right-radius: 100px;
  -moz-border-radius: 20px;
  -moz-border-radius-bottomright: 100px;
  border-radius: 20px;
  border-bottom-right-radius: 100px;
  min-height: 350px;
}

.parent .parent-child:hover{
  background-color: #1d8f3d;
  -webkit-border-radius: 20px;
  -webkit-border-bottom-right-radius: 20px;
  -moz-border-radius: 20px;
  -moz-border-radius-bottomright: 20px;
  border-radius: 20px;
  border-bottom-right-radius: 20px;
}

.counter {
  padding: 10px;
  color: white;
  background-color: #2ea44f;
  border: 1px solid rgba(27, 31, 35, .15);
  border-radius: 6px;
  display: inline-block;
  margin-bottom: 10px;
}

.button-3 {
  appearance: none;
  background-color: #2ea44f;
  border: 1px solid rgba(27, 31, 35, .15);
  border-radius: 6px;
  box-shadow: rgba(27, 31, 35, .1) 0 1px 0;
  box-sizing: border-box;
  color: #fff;
  cursor: pointer;
  display: inline-block;
  font-family: -apple-system,system-ui,"Segoe UI",Helvetica,Arial,sans-serif,"Apple Color Emoji","Segoe UI Emoji";
  font-size: 14px;
  font-weight: 600;
  line-height: 20px;
  padding: 6px 16px;
  position: relative;
  text-align: center;
  text-decoration: none;
  user-select: none;
  -webkit-user-select: none;
  touch-action: manipulation;
  vertical-align: middle;
  white-space: nowrap;
}

.button-3:hover {
  background-color: #2c974b;
}

.button-3:disabled {
  background-color: #94d3a2;
  border-color: rgba(27, 31, 35, .1);
  color: rgba(255, 255, 255, .8);
  cursor: default;
}

.button-3:active {
  background-color: #298e46;
  box-shadow: rgba(20, 70, 32, .2) 0 1px 0 inset;
}

@media (max-width: 900px) {
  .parent-child-internal {
    min-height: 0px;
  }
  .parent {
    grid-template-columns: repeat(1, 1fr);
    grid-template-rows: repeat(1, 1fr);
}
}
</style>
