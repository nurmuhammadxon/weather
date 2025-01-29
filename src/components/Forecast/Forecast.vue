<template>
    <div class="forecast">
        <div>
            <h2 class="text-[20px] text-white uppercase">
                {{ 'Ob havo haqida' }}
            </h2>
            <ul class="w-full">
                <li class="my-[30px] flex items-center justify-between">
                    <span class="text-[#ffffffB3] text-[18px]">Temp max</span>
                    <!-- tempratura max -->
                    <span class="text-[#fff] text-[18px]">
                        {{ maxTemp }}
                        <i class='bx bxs-thermometer text-[24px] text-red-400'></i>
                    </span>
                </li>
                <li class="my-[30px] flex items-center justify-between">
                    <span class="text-[#ffffffB3] text-[18px]">Temp min</span>
                    <!-- tempratura min -->
                    <span class="text-[#fff] text-[18px]">
                        {{ minTemp }}
                        <i class='bx bxs-thermometer text-[24px] text-blue-400'></i>
                    </span>
                </li>
                <li class="my-[30px] flex items-center justify-between">
                    <span class="text-[#ffffffB3] text-[18px]">Namlik</span>
                    <!-- namlik %da -->
                    <span class="text-[#fff] text-[18px]">
                        {{ humidity }}
                        <i class='bx bxs-droplet-half text-[24px] text-blue-300'></i>
                    </span>
                </li>
                <li class="my-[30px] flex items-center justify-between">
                    <span class="text-[#ffffffB3] text-[18px]">Bulutli</span>
                    <!-- Bulutlilik %da -->
                    <span class="text-[#fff] text-[18px]">
                        {{ cloud }}
                        <i class='bx bxl-soundcloud text-[26px] text-white'></i>
                    </span>
                </li>
                <li class="my-[30px] flex items-center justify-between">
                    <span class="text-[#ffffffB3] text-[18px]">Shamol</span>
                    <!-- Shamol km/h da -->
                    <span class="text-[#fff] text-[18px]">
                        {{ wind }}
                        <i class='bx bx-wind text-[24px] text-white'></i>
                    </span>
                </li>
            </ul>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        maxTemp: {
            type: Number,
            required: true,
        },
        minTemp: {
            type: Number,
            required: true,
        },
        humidity: {
            type: Number,
            required: true,
        },
        cloud: {
            type: Number,
            required: true,
        },
        wind: {
            type: Number,
            required: true,
        },
    },
}
</script>

<style>
.forecast {
    width: 354px;
    margin-top: 50px;
}
</style>