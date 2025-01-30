<template>
    <div class="app" :class="weatherClass">
        <!-- left content -->
        <div class="left-content">
            <!-- Logo -->
            <div class="logo">
                <a href="./App.vue" class="flex font-bold text-4xl">
                    <!-- <svg width="90" height="50" viewBox="0 0 90 47" fill="none" xmlns="http://www.w3.org/2000/svg">
                        <path fill-rule="evenodd" clip-rule="evenodd"
                            d="M71.834 1.67818L78.1206 3.36365L73.2061 19.8301L82.4689 16.8415L77.6172 31.1032L72.7656 45.3649L66.5523 43.4497L69.3758 35.1498L72.1993 26.85L63.4818 29.6626L71.834 1.67818Z"
                            fill="url(#paint0_linear_129_5353)" />
                        <path fill-rule="evenodd" clip-rule="evenodd"
                            d="M66.2442 12.0463L62.7186 24.6071L60.186 15.9889L53.262 39.5811H51.1666H48.091H45.083L35.8225 3.02905H45.2182L50.0006 26.8109L56.6756 3.02905H57.5881H62.8605H63.7055L66.2442 12.0463Z"
                            fill="white" />
                        <path fill-rule="evenodd" clip-rule="evenodd"
                            d="M36.6489 15.7167L41.0176 32.9604L39.3325 39.6477H36.3691H33.3047H31.1831L24.2752 16.0126L17.3764 39.6477H15.2885H12.2241H9.22698L0 3.02905H9.36168L14.1267 26.8542L20.7775 3.02905H21.6868H26.9401H27.782L34.446 26.8285L36.6489 15.7167Z"
                            fill="#CACACA" />
                        <defs>
                            <linearGradient id="paint0_linear_129_5353" x1="65.9395" y1="3.57995" x2="78.7935"
                                y2="43.4201" gradientUnits="userSpaceOnUse">
                                <stop stop-color="#F5BD52" />
                                <stop offset="1" stop-color="#F5DA79" />
                            </linearGradient>
                        </defs>
                    </svg> -->
                    <span class="text-blue-400">
                        Muhid
                    </span>
                    <span class="text-red-400">dinov</span>
                </a>
            </div>
            <WeatherCard :temperature="weatherData.temp" :city="weatherData.city" />
            <WeatherDetails :weatherType="weatherData.weatherType" />
        </div>
        <!-- Right content -->
        <div class="rigth-content">
            <SearchBar @SearchCity="updateCity" />
            <Forecast :maxTemp="weatherData.maxTemp" :minTemp="weatherData.minTemp" :humidity="weatherData.namlik"
                :cloud="weatherData.cloud" :wind="weatherData.wind" />
        </div>
    </div>
</template>

<script>
import Forecast from '../Forecast/Forecast.vue'
import SearchBar from '../SearchBar/SearchBar.vue'
import WeatherCard from '../WeatherCard/WeatherCard.vue'
import WeatherDetails from '../WeatherDetails/WeatherDetails.vue'
export default {
    data() {
        return {
            apiKey: '1bed523ec934e0dd8869dc32fe7b9ce9',
            apiURL: 'https://api.openweathermap.org/data/2.5/weather?units=metric&q=',
            weatherData: {
                temp: 0,
                city: "Yuklanmoqda...",
                maxTemp: 0,
                minTemp: 0,
                cloud: 0,
                wind: 0,
                namlik: 0,
                weatherType: 'Clear'
            },
        }
    },
    components: {
        WeatherCard,
        WeatherDetails,
        SearchBar,
        Forecast,
    },
    computed: {
        weatherClass() {
            let month = new Date().getMonth() + 1
            if ([12, 1, 2].includes(month)) return 'bg-winter'
            if ([3, 4, 5].includes(month)) return 'bg-spring'
            if ([6, 7, 8].includes(month)) return 'bg-summer'
            if ([9, 10, 11].includes(month)) return 'bg-autumn'
            return ''
        }
    },
    methods: {
        async WeatherNow(city = "Samarkand") {
            try {
                const response = await fetch(this.apiURL + city + '&appid=' + this.apiKey)
                const data = await response.json()

                this.weatherData.temp = Math.round(data.main.temp)
                this.weatherData.city = data.name
                this.weatherData.maxTemp = Math.round(data.main.temp_max)
                this.weatherData.minTemp = Math.round(data.main.temp_min)
                this.weatherData.cloud = data.clouds.all
                this.weatherData.wind = data.wind.speed
                this.weatherData.namlik = data.main.humidity
                this.weatherData.weatherType = data.weather[0].main
            } catch (error) {
                alert(error.message)
            }
        },
        updateCity(newCity) {
            this.weatherData.city = newCity
            this.WeatherNow(newCity)
        },
    },
    mounted() {
        this.WeatherNow()
    }
}
</script>

<style scoped>
.app {
    width: 100%;
    height: 100vh;
    margin: 0 auto;
    display: flex;
    align-items: center;
    justify-content: space-between;
    position: relative;
}

.logo {
    width: 90px;
    height: 50px;
    display: flex;
    align-items: center;
    justify-content: center;
    position: absolute;
    top: 40px;
    left: 120px;
}


.left-content {
    display: flex;
    align-items: end;
}

.rigth-content {
    max-width: 526px;
    width: 100%;
    height: 100vh;
    margin-left: auto;
    padding-left: 35px;
    backdrop-filter: blur(19px);
    border-left: 2px solid #ffffff23;
}

.bg-winter {
    background: linear-gradient(rgba(0, 0, 0, 0.3), rgba(0, 0, 0, 0.3)), url('@/images/bg-winter.jpg') no-repeat center/cover;
}

.bg-spring {
    background: linear-gradient(rgba(0, 0, 0, 0.3), rgba(0, 0, 0, 0.3)), url('@/images/bg-spring.jpg') no-repeat center/cover;
}

.bg-summer {
    background: linear-gradient(rgba(0, 0, 0, 0.3), rgba(0, 0, 0, 0.3)), url('@/images/bg-summer.jpg') no-repeat center/cover;
}

.bg-autumn {
    background: linear-gradient(rgba(0, 0, 0, 0.3), rgba(0, 0, 0, 0.3)), url('@/images/bg-autumn.jpg') no-repeat center/cover;
}
</style>