<template>
	<div class="container">
		<div class="weather-side">
			<div class="weather-gradient"></div>
			<div class="date-container">
				<h2 class="date-dayname">{{ getDate.weekday }}</h2>
				<span class="date-day">{{ getDate.date }}</span
				><i class="location-icon fas fa-map-marker-alt"></i>
				<span class="location">Paris, FR</span>
			</div>

			<div class="weather-container">
				<i class="weather-icon far fa-sun"></i>
				<h1 class="weather-temp">29°C</h1>
				<h3 class="weather-desc">Sunny</h3>
			</div>
		</div>

		<div class="info-side">
			<div class="today-info-container">
				<div class="today-info">
					<div class="precipitation">
						<span class="title">PRECIPITATION</span><span class="value">0 %</span>
						<div class="clear"></div>
					</div>
					<div class="humidity">
						<span class="title">HUMIDITY</span><span class="value">34 %</span>
						<div class="clear"></div>
					</div>
					<div class="wind">
						<span class="title">WIND</span><span class="value">0 km/h</span>
						<div class="clear"></div>
					</div>
				</div>
			</div>

			<div class="week-container">
				<ul class="week-list">
					<li class="active">
						<i class="day-icon far fa-sun"></i>
						<span class="day-name">Tue</span><span class="day-temp">29°C</span>
					</li>
					<li>
						<i class="day-icon fas fa-cloud"></i>
						<span class="day-name">Wed</span><span class="day-temp">21°C</span>
					</li>
					<li>
						<i class="day-icon fas fa-cloud-meatball"></i><span class="day-name">Thu</span><span class="day-temp">08°C</span>
					</li>
					<li>
						<i class="day-icon fas fa-cloud-showers-heavy"></i><span class="day-name">Fry</span
						><span class="day-temp">19°C</span>
					</li>
					<div class="clear"></div>
				</ul>
			</div>

			<div class="location-container">
				<button class="location-button"><i data-feather="map-pin"></i><span>Change location</span></button>
			</div>
		</div>
	</div>
</template>

<script>
export default {
	name: "App",
	data: () => ({
		API_URL: "pro.openweathermap.org/data/2.5/forecast/hourly",
	}),
	computed: {
		getDate: function () {
			const d = new Date();
			const monthNames = [
				"January",
				"February",
				"March",
				"April",
				"May",
				"June",
				"July",
				"August",
				"September",
				"October",
				"November",
				"December",
			];
			const month = d.getMonth() + 1;
			const weekday = ["Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"][d.getDay()];
			const date = `${d.getDate()}, ${monthNames[month]} ${d.getFullYear()}`;

			return { date, weekday };
		},
	},
};
</script>

<style lang="scss">
#app {
	font-family: Avenir, Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
}
@import url("https://fonts.googleapis.com/css?family=Montserrat:400,700,900&display=swap");

:root {
	--gradient: linear-gradient(135deg, #72edf2 10%, #5151e5 100%);
}

* {
	-webkit-box-sizing: border-box;
	box-sizing: border-box;
	line-height: 1.25em;
}

.clear {
	clear: both;
}

body {
	margin: 0;
	width: 100%;
	height: 100vh;
	font-family: "Montserrat", sans-serif;
	background-color: #343d4b;
	display: -webkit-box;
	display: -ms-flexbox;
	display: flex;
	-webkit-box-align: center;
	-ms-flex-align: center;
	align-items: center;
	-webkit-box-pack: center;
	-ms-flex-pack: center;
	justify-content: center;
}

.container {
	border-radius: 25px;
	-webkit-box-shadow: 0 0 70px -10px rgba(0, 0, 0, 0.2);
	box-shadow: 0 0 70px -10px rgba(0, 0, 0, 0.2);
	background-color: #222831;
	color: #ffffff;
	height: 400px;
}

.weather-side {
	position: relative;
	height: 100%;
	border-radius: 25px;
	background-image: url("https://images.unsplash.com/photo-1559963110-71b394e7494d?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=675&q=80");
	width: 300px;
	-webkit-box-shadow: 0 0 20px -10px rgba(0, 0, 0, 0.2);
	box-shadow: 0 0 20px -10px rgba(0, 0, 0, 0.2);
	float: left;
	-webkit-transform: scale(1.1) perspective(1500px) rotateY(10deg);
	transform: scale(1.1) perspective(1500px) rotateY(10deg);
}

.weather-gradient {
	position: absolute;
	width: 100%;
	height: 100%;
	top: 0;
	left: 0;
	background-image: var(--gradient);
	border-radius: 25px;
	opacity: 0.8;
}

.date-container {
	position: absolute;
	top: 25px;
	left: 25px;
}

.date-dayname {
	margin: 0;
}

.date-day {
	display: block;
}

.location {
	display: inline-block;
	margin-top: 10px;
}

.location-icon {
	display: inline-block;
	font-size: 0.8em;
	margin-right: 7px;
	margin-bottom: 2px;
}

.weather-container {
	position: absolute;
	bottom: 25px;
	left: 25px;
}

.weather-icon {
	font-size: 60px;
}

.weather-temp {
	margin: 0;
	font-weight: 700;
	font-size: 4em;
}

.weather-desc {
	margin: 0;
}

.info-side {
	position: relative;
	float: left;
	height: 100%;
	padding-top: 25px;
}

.today-info {
	padding: 15px;
	margin: 0 25px 25px 25px;
	/* 	box-shadow: 0 0 50px -5px rgba(0, 0, 0, 0.25); */
	border-radius: 10px;
}

.today-info > div:not(:last-child) {
	margin: 0 0 10px 0;
}

.today-info > div .title {
	float: left;
	font-weight: 700;
}

.today-info > div .value {
	float: right;
}

.week-list {
	list-style-type: none;
	padding: 0;
	margin: 10px 35px;
	-webkit-box-shadow: 0 0 50px -5px rgba(0, 0, 0, 0.25);
	box-shadow: 0 0 50px -5px rgba(0, 0, 0, 0.25);
	border-radius: 10px;
}

.week-list > li {
	float: left;
	padding: 15px;
	transition: 200ms ease;
	border-radius: 10px;
}

.week-list > li.active {
	background: #fff;
	color: #222831;
	border-radius: 10px;
}

.week-list > li .day-name {
	display: block;
	margin: 10px 0 0 0;
	text-align: center;
}

.week-list > li .day-icon {
	display: block;
	height: 30px;
	width: auto;
	margin: 0 auto;
}

.week-list > li .day-temp {
	display: block;
	text-align: center;
	margin: 10px 0 0 0;
	font-weight: 700;
}

.location-container {
	padding: 25px 35px;
}

.location-button {
	outline: none;
	width: 100%;
	-webkit-box-sizing: border-box;
	box-sizing: border-box;
	border: none;
	border-radius: 25px;
	padding: 10px;
	font-family: "Montserrat", sans-serif;
	background-image: var(--gradient);
	color: #ffffff;
	font-weight: 700;
	-webkit-box-shadow: 0 0 30px -5px rgba(0, 0, 0, 0.25);
	box-shadow: 0 0 30px -5px rgba(0, 0, 0, 0.25);
	cursor: pointer;
	-webkit-transition: -webkit-transform 200ms ease;
	transition: -webkit-transform 200ms ease;
	-o-transition: transform 200ms ease;
	transition: transform 200ms ease;
	transition: transform 200ms ease, -webkit-transform 200ms ease;
}

.location-button:hover {
	-webkit-transform: scale(0.95);
	-ms-transform: scale(0.95);
	transform: scale(0.95);
}

.location-button .feather {
	height: 1em;
	width: auto;
	margin-right: 5px;
}
</style>
