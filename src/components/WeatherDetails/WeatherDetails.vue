<template>
    <div class="ml-2.5">
        <!-- havo turi -->
        <p v-html="weatherType('quyoshli')" class="text-white text-8xl"></p>
    </div>
</template>

<script>
export default {
    data() {
        return {

        }
    },
    methods: {
        weatherType(textType) {
            switch (textType) {
                case "quyoshli":
                    return "<i class='bx bx-sun'></i>"
                case "bulutli":
                    return "<i class='bx bx-cloud'></i>"
                case "yomg'irli":
                    return "<i class='bx bx-cloud-rain'></i>"
                case "qorli":
                    return "<i class='bx bx-cloud-snow'></i>"
                case "shamolli":
                    return "<i class='bx bx-wind'></i>"
                default:
                    return "<i class='bx bxs-sun'></i>"
            }
        }
    },
}
</script>

<style></style>
