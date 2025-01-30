<template>
    <div class="ml-2.5">
        <!-- havo turi -->
        <p v-html="getWeatherIcon(weatherType)" class="text-white text-8xl"></p>
    </div>
</template>

<script>
export default {
    props: {
        weatherType: {
            type: String,
            required: true,
        }
    },
    data() {
        return {

        }
    },
    methods: {
        getWeatherIcon(textType) {
            switch (textType) {
                case "Clear":
                    return "<i class='bx bx-sun'></i>"
                case "Clouds":
                    return "<i class='bx bx-cloud'></i>"
                case "Drizzle":
                    return "<i class='bx bx-cloud-rain'></i>"
                case "Rain":
                    return "<i class='bx bx-cloud-snow'></i>"
                case "Mist":
                    return "<i class='bx bx-wind'></i>"
            }
        }
    },
}
</script>

<style></style>
