---
layout: post
title: Design Focus
---
I was recently connected with a marketing and social media services company. It was in demand for a new web developer. As part of their interview process, they had asked me to present to them how I would redesign their website. Here is a small example of what I had in mind. The entire website is not complete, but you'll get the idea.

I first constructed the html skeleton for the website.
```
<!DOCTYPE html>
<html>
    <head>
      <meta charset="UTF-8">
      <meta name="viewport" content="width=device-width,
      initial-scale=1.0">
      <meta http-equiv="X-UA-Compatible" content="ie=edge">
      <link href="https://fonts.googleapis.com/css?family=Noto+Serif+SC" rel="stylesheet">
      <link href="https://fonts.googleapis.com/css?family=Major+Mono+Display" rel="stylesheet">
      <link href="https://fonts.googleapis.com/css?family=Bungee+Inline|Bungee+Shade|Codystar|Limelight|Monoton|Poppins|Raleway+Dots|Vast+Shadow" rel="stylesheet">
      <link rel="stylesheet" href="assets/styles/main.css">
      <title>S P E A Q</title>
    </head>
    <body>
      <header class="v-header container" id="sec0">
        <div class="fullscreen-video-wrap">
          <video src="assets/videos/vidcamera.mp4" autoplay loop muted>
          </video>
        </div>
        <div class="header-overlay"></div>
          <nav>
            <div class="logo">
              <h1>SPEAQ</h1>
            </div>
            <ul class="menu">
              <li><a href="#sec0">Home</a></li>
              <li><a href="#sec1">Portolio</a></li>
              <li><a href="#sec2">Services</a></li>
              <li><a href="#sec3">About</a></li>
              <li><a href="#sec4">Contact Us</a></li>
            </ul>
            <div class="burger">
              <div class="line1">
              </div>
              <div class="line2">
              </div>
              <div class="line3">
              </div>
          </nav>

        <div class="header-content text-md-center">
          <a class="btn">Create to Inspire. Inspire to Create.</a>
        </div>
      </header>


      <section id="sec1">
          <div class="row">
              <div class="column">
                <a href="user-story-1.html">
                <img src="assets/images/adventure-aerial-aerial-photography-1122408.jpg">
              </a>
              </div>
              <div class="column">
                <img src="assets/images/beverages-brunch-cocktail-5317.jpg">
              </div>
              <div class="column">
                <img src="assets/images/app-bridge-gadget-122383.jpg">
              </div>
              <div class="column">
                <img src="assets/images/aerial-background-beverage-990820.jpg">
              </div>
              <div class="column">
                <img src="assets/images/aroma-art-beverage-1251175.jpg">
              </div>
              <div class="column">
                <img src="assets/images/architecture-contemporary-flowers-704982.jpg">
              </div>
              <div class="column">
                <img src="assets/images/barbecue-bbq-berries-1667580.jpg">
              </div>
              <!-- <img src="assets/images/app-blurred-background-cellphone-1092671.jpg" class="fit-image">
              <img src="assets/images/adventure-boat-freedom-1223649.jpg" class="fit-image">
              <img src="assets/images/blur-breakfast-cocktail-316891.jpg" class="fit-image">
              <img src="assets/images/boat-daylight-hd-wallpaper-675764.jpg" class="fit-image">
              <img src="assets/images/bottle-drink-glass-113734.jpg" class="fit-image">
              <img src="assets/images/cheers-drink-group-544961.jpg" class="fit-image"> -->
            </div>
      </section>
      <section id="sec2" data-text="Services"></section>
      <section id="sec3" data-text="About"></section>
      <section id="sec4" data-text="Contact Us"></section>

      <script src="scripts/main.js"></script>

    </body>
</html>
```

I included a second page for the website so that viewers can get a grasp of what the completed site would feel and look like.

```

<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width,
    initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <link href="https://fonts.googleapis.com/css?family=Noto+Serif+SC" rel="stylesheet">
    <link href="https://fonts.googleapis.com/css?family=Major+Mono+Display" rel="stylesheet">
    <link href="https://fonts.googleapis.com/css?family=Bungee+Inline|Bungee+Shade|Codystar|Limelight|Monoton|Poppins|Raleway+Dots|Vast+Shadow" rel="stylesheet">
    <link rel="stylesheet" href="assets/styles/user-story-1.css">
    <title>S P E A Q</title>
  </head>
  <body>

    <header class="v-header container">
      <div class="fullscreen-image-wrap">
        <img src="assets/images/adventure-aerial-aerial-photography-1122408.jpg">
      </div>
      <div class="header-overlay"></div>
        <nav>
          <div class="logo">
            <h1>SPEAQ</h1>
          </div>
          <ul class="menu">
            <li><a href="home.html#sec0">Home</a></li>
            <li><a href="home.html#sec1">Portolio</a></li>
            <li><a href="home.html#sec2">Services</a></li>
            <li><a href="home.html#sec3">About</a></li>
            <li><a href="home.html#sec4">Contact Us</a></li>
          </ul>
          <div class="burger">
            <div class="line1">
            </div>
            <div class="line2">
            </div>
            <div class="line3">
            </div>
        </nav>
        <div class="header-title">
          <h2>London Boat Rentals<h2>
          <h5>Immersive digital content</h5>
          <h6>Branding</h6>
          <h6>UX/UI Design</h6>
          <h6>Web Application Development</h6>
        </div>

    </header>
    <section>
      <div class="company-details">
        <p>Lorem ipsum dolor sit amet, mea iudico tempor an, at pri fastidii salutandi, mea quando constituam ei. Dissentias signiferumque conclusionemque sit te. Assum nobis timeam et per, cum commodo malorum nostrum ut. Viris partiendo necessitatibus quo et. Sea te hendrerit posidonium, quo te invidunt conclusionemque. Vis elit maiorum oporteat et.</p>
      </div>
      <div class="company-images">

        <img src="assets/images/03-3.jpg" class="companyimage2">
      </div>
    </section>
    <section></section>
    <section></section>

  </body>

```

The important part about this is that I only utilized HTML and CSS to create this mockup.
This is my main.css file

```
*, *::before, *::after {
    -moz-box-sizing: border-box;
    -webkit-box-sizing: border-box;
    box-sizing: border-box;
}
html{
  scroll-behavior: smooth;
}
/* Medium screens (640px) */
@media (min-width: 640px) {
    html { font-size: 112%; }
}

/* Large screens (1024px) */
@media (min-width: 1024px) {
    html { font-size: 120%; }
}


body{
  margin:0;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  font-size:1rem;
  font-weight:normal;
  line-height:1.5;
  color:#333;
  overflow-x:hidden;
}

.v-header{
  height:100vh;
  display:flex;
  align-items:center;
  color:#fff;
}

.container{
  max-width:960px;
  padding-left:1rem;
  padding-right:1rem;
  margin:auto;
  text-align:center;
}


.fullscreen-video-wrap{
  position: absolute;
  top: 0; right: 0; bottom: 0; left: 0;
  overflow: hidden;

}

.fullscreen-video-wrap video{
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: -1;

}


@media (min-aspect-ratio: 16/9) {
  .fullscreen-video-wrap video { height: 300%; top: -100%; }
}
@media (max-aspect-ratio: 16/9) {
  .fullscreen-video-wrap video { width: 300%; left: -100%; }
}
@supports (object-fit: cover) {
  .fullscreen-video-wrap video{
    top: 0; left: 0;
    width: 100%; height: 100%;
    object-fit: cover;
  }
}

nav {

  display: flex;
  width: 100%;
  height: 70px;
  color: white;
  justify-content: space-around;
  align-items: center;
  height: 8vh;
  position: absolute;
  top:0;
  left:0;
  z-index:2;
}


.logo{
  font-family: "Codystar";
  font-size: 1.5rem;
  z-index: 2;
  text-transform: uppercase;
  letter-spacing: 20px;
  color: white;
  padding-top: 60px;


}
.menu{

  display: flex;
  justify-content: space-around;
  width: 70%;
  z-index: 1;
  padding-top: 60px;

}
.menu li{

  float:left;
  width:120px;
  height: 40px;
  line-height: 40px;
  text-align: center;
  list-style: none;
}
.menu li a{

  color: white;
  text-decoration: none;
  font-family: "Poppins";
  text-transform: uppercase;
  display:block;
}

.menu li a:hover{
  color: #4a5e81;
}

.burger{
  display: none;
}

.burger div {
  width: 25px;
  height: 3px;
  background-color: white;
  margin: 5px;
}

@media screen and (max-width: 1024px){
  .menu {
    width: 80%;
  }
}

@media screen and (max-width: 768px){
  .menu {
    position: absolute;
    right: 0px;
    height: 92vh;
    top: 8vh;
    background-color: black;
    display: flex;
    flex-direction: column;
    align-items: center;
    z-index: 2;
  }
}
.header-overlay{
  height:100vh;
  position: absolute;
  top:0;
  left:0;
  width:100vw;
  z-index:1;
  /* background:#5F9EA0; */
  background-color: black;
  opacity:0.45;
}


.header-content{
  z-index:1;
}


.header-content .btn{
  font-family: "Poppins";
  font-size:1.5rem;
  display:block;
  padding-bottom:2rem

}

.btn{
  background: none;
  text-align: center;
  color:#fff;
  font-size:0.5rem;
  padding: 0rem 1rem;
  text-decoration: none;
  position: absolute;
  top: 50%;
  left: 50%;
  margin-right: -50%;
  transform: translate(-50%, -50%)
}

section{

  height:100vh;
  display: flex;
  justify-content: center;
  align-items: center;

}

section:nth-child(odd){
  background:#ccc;

}

section:before{
  content: attr(data-text);
  color: #262626;
  font-size: 8rem;
}

#sec1 {
  width: 100%;
  height: 100%;
  background-color: black;
}

.row {
  display: flex;
  flex-wrap: wrap;
  align-content: flex-start;
  justify-content: space-between;
  padding: 0 4px;
}

/* Create four equal columns that sits next to each other */
.column {
  float: left;
  width: 50%;
  padding: 5px;

}
.row::after {
  content: "";
  clear: both;
  display: table;
}

.column img {
  margin-top: 8px;
  vertical-align: middle;
  max-width: 100%;
  max-height: 100%;
  float:left;
  margin-bottom: 15px;
  transition: 0.9s ease;
  -webkit-filter: grayscale(1); /* Webkit Nightlies & Chrome Canary */
  -webkit-transition: all .8s ease-in-out;

}

.column img:hover{
  box-shadow: 0 10px 40px 0 rgba(0,0,0,0.5);
  transition: 0.8s ease;
  filter: none;
      -webkit-filter: grayscale(0);
      -webkit-transform: scale(1.01);
    }
}



/* Responsive layout - makes a two column-layout instead of four columns */
@media screen and (max-width: 800px) {
  .column {
    flex: 50%;
    max-width: 50%;
  }
}

/* Responsive layout - makes the two columns stack on top of each other instead of next to each other */
@media screen and (max-width: 600px) {
  .column {
    flex: 100%;
    max-width: 100%;
  }
}

@media(max-width:960px){
  .container{
    padding-right:3rem;
    padding-left:3rem;
  }
}
```
This is the CSS file for my second example page.

```
*, *::before, *::after {
    -moz-box-sizing: border-box;
    -webkit-box-sizing: border-box;
    box-sizing: border-box;
}
html{
  scroll-behavior: smooth;
}
/* Medium screens (640px) */
@media (min-width: 640px) {
    html { font-size: 112%; }
}

/* Large screens (1024px) */
@media (min-width: 1024px) {
    html { font-size: 120%; }
}


body{
  margin:0;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  font-size:1rem;
  font-weight:normal;
  line-height:1.5;
  color:#333;
  overflow-x:hidden;
}

.v-header{
  height:100vh;
  display:flex;
  align-items:center;
  color:#fff;
}

.container{
  max-width:960px;
  padding-left:1rem;
  padding-right:1rem;
  margin:auto;
  text-align:center;
}


.fullscreen-image-wrap{
  position: absolute;
  top: 0; right: 0; bottom: 0; left: 0;
  overflow: hidden;

}

.fullscreen-image-wrap img{
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: -1;
  position: fixed;

}


nav {

  display: flex;
  width: 100%;
  height: 70px;
  color: white;
  justify-content: space-around;
  align-items: center;
  height: 8vh;
  position: absolute;
  top:0;
  left:0;
  z-index:2;
}


.logo{
  font-family: "Codystar";
  font-size: 1.5rem;
  z-index: 2;
  text-transform: uppercase;
  letter-spacing: 20px;
  color: white;
  padding-top: 60px;


}
.menu{

  display: flex;
  justify-content: space-around;
  width: 70%;
  z-index: 1;
  padding-top: 60px;

}
.menu li{

  float:left;
  width:120px;
  height: 40px;
  line-height: 40px;
  text-align: center;
  list-style: none;
}
.menu li a{

  color: white;
  text-decoration: none;
  font-family: "Poppins";
  text-transform: uppercase;
  display:block;
}

.menu li a:hover{
  color: #4a5e81;
}

.burger{
  display: none;
}

.burger div {
  width: 25px;
  height: 3px;
  background-color: white;
  margin: 5px;
}

@media screen and (max-width: 1024px){
  .menu {
    width: 80%;
  }
}

@media screen and (max-width: 768px){
  .menu {
    position: absolute;
    right: 0px;
    height: 92vh;
    top: 8vh;
    background-color: white;
    display: flex;
    flex-direction: column;
    align-items: center;
    z-index: 2;
  }

  .menu li a{

    color: black;
    text-decoration: none;
    font-family: "Poppins";
    text-transform: uppercase;
    display:block;
  }

  .menu li a:hover{
    color: #4a5e81;
  }
}
.header-overlay{
  height:100vh;
  position: absolute;
  top:0;
  left:0;
  width:100vw;
  z-index:1;
  /* background:#5F9EA0; */
  background-color: black;
  opacity:0.45;
}


.header-content{
  z-index:1;
}


.header-content .btn{
  font-family: "Poppins";
  font-size:1.5rem;
  display:block;
  padding-bottom:2rem

}

.btn{
  background: none;
  text-align: center;
  color:#fff;
  font-size:0.5rem;
  padding: 0rem 1rem;
  text-decoration: none;
  position: absolute;
  top: 50%;
  left: 50%;
  margin-right: -50%;
  transform: translate(-50%, -50%)
}

.header-title{
  color: white;
  z-index: 1;
  font-family: "Poppins";
}
.header-title h2{
  font-family: "Major Mono Display";
  font-size: 3rem;

}

section{

  height:100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #303030;
  opacity:0.85;

}

section:before{
  content: attr(data-text);
  color: #262626;
  font-size: 8rem;
}

section p {
  z-index: 3;
  color: white;
  margin-left:5;
  text-align: center;
}

section .companyimage2{


  width:100%;
  height:100%;
  overflow:hidden;
  opacity: 1;

}


@media(max-width:960px){
  .container{
    padding-right:3rem;
    padding-left:3rem;
  }
}
```

<iframe width="420" height="315" src="http://www.youtube.com/embed/dQw4w9WgXcQ" frameborder="0" allowfullscreen></iframe> 


> Suspendisse lectus leo, consectetur in tempor sit amet, placerat quis neque

Etiam luctus porttitor lorem, sed suscipit est rutrum non. Curabitur lobortis nisl a enim congue semper. Aenean commodo ultrices imperdiet. Vestibulum ut justo vel sapien venenatis tincidunt.

Phasellus eget dolor sit amet ipsum dapibus condimentum vitae quis lectus. Aliquam ut massa in turpis dapibus convallis. Praesent elit lacus, vestibulum at malesuada et, ornare et est. Ut augue nunc, sodales ut euismod non, adipiscing vitae orci. Mauris ut placerat justo. Mauris in ultricies enim. Quisque nec est eleifend nulla ultrices egestas quis ut quam. Donec sollicitudin lectus a mauris pulvinar id aliquam urna cursus. Cras quis ligula sem, vel elementum mi. Phasellus non ullamcorper urna.
