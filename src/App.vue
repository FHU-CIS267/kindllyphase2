<template>
  <div id="app">
    <header>
      <div class="container">
        <div class="left">
          <router-link to="/"><h1>Kindlly</h1></router-link>
          <p>create kindness, get points</p>
        </div>
        <nav>
          <ul>
            <li class="nav-item"><router-link to="/about">Contribute</router-link></li>
			<li class="nav-item"><a href="#">Favorites</a></li>
            <li class="nav-item">
              <a href="#" id="profile-link">
                <img src="@/assets/img/male-square.png" alt="">
                <p class="points">
                  <span class="value">300</span>
                  <span class="label">KP</span>
                </p>
              </a>
            </li>
          </ul>
        </nav>
      </div>
    </header>
    <router-view/>
  </div>
</template>

<style>
@import url('assets/css/elusive-icons.min.css');

* {
	margin: 0;
	padding: 0;
	box-sizing: border-box;
}

body {
	font-family: Roboto, sans-serif;
	background: #f2eccf;
	color: #003049;
	font-size: 18px;
}

.container {
	max-width: 900px;
	margin: 0 auto;
}

h1,
h2,
h3 {
	font-family: "Playfair Display";
}

h4 {
	font-weight: 800;
}

header {
	border-bottom: 1px solid #f77f00;
	color: #003049;
	height: 6rem;
	position: fixed;
	width: 100%;
	background: #f2eccf;
	top: 0;
	left: 0;
	z-index: 10;
}

header h1 {
	color: #003049;
	font-size: 3rem;
}

header a {
	text-decoration: none;
	display: block;
}

header p {
	font-size: 1rem;
	font-weight: 100;
}

header .container {
	display: flex;
}

header nav {
	margin-left: auto;
	display: flex;
}

header nav ul {
	list-style: none;
	display: flex;
}

header nav ul li {
	margin: 1rem 1rem;
	font-size: 1.2rem;
	font-family: "Playfair Display";
}

header nav ul li a {
	color: #003049;
}

#profile-link {
	display: flex;
	position: relative;
	height: 3rem;
	margin: 0 0;
	right: -2rem;
}

#profile-link img {
	display: flex;
	height: 4rem;
	width: 4rem;
	border-radius: 2rem;
	margin: 0;
	padding: 0;
	border: 1px solid #f77f00;

	/* z-index: 10; */
}

#profile-link .points {
	display: block;
	margin: 0;
	display: flex;
	flex-direction: column;
	font-family: Roboto, sans-serif;
	font-size: 1.5rem;
	font-weight: 800;
	line-height: 1.1rem;
	padding-top: 1.2rem;
	background: #d62828;
	color: #eee;
	width: 4rem;
	height: 4rem;
	border-radius: 2rem;
	text-align: center;
	position: relative;
	left: -1rem;
}

#profile-link .points .label {
	font-size: 0.6666666em;
	font-weight: 200;
}
</style>
