<template>
    <div class="flex items-end justify-center ml-[120px]">
        <!-- harorat -->
        <div class="flex items-end justify-center">
            <p class="text-white text-8xl font-medium ">
                <!-- {{ timperatura }} -->
                {{ temperature }}°C
            </p>
        </div>
        <div class="flex flex-col ml-[15px]">
            <!-- joylashgan shahar nomi -->
            <h1 class="text-white text-[48px] font-medium">
                {{ city }}
                <!-- {{ city }} -->
            </h1>
            <!-- vaqt -->
            <p class="text-white text-[24px] font-[300]">
                {{ time }}
            </p>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        temperature: {
            type: Number,
            required: true,
        },
        city: {
            type: String,
            required: true
        },
    },
    data() {
        return {
            time: '',
        }
    },
    component: {
        WeatherNow: {
            type: Object,
            required: true,
        }
    },
    methods: {
        now() {
            let haftaKunlari = ['Yakshanba', 'Dushanba', 'Seshanba', 'Chorshanba', 'Payshanba', 'Juma', 'Shanba']
            let OyNomlari = ['Yanvar', 'Fevral', 'Mart', 'Aprel', 'May', 'Iyun', 'Iyul', 'Avgust', 'Sentabr', 'Noyabr', 'Dekabr']
            let today = new Date()

            let soat = today.getHours().toString().padStart(2, '0')
            let minut = today.getMinutes().toString().padStart(2, '0')
            let haftaKuni = haftaKunlari[today.getDay()]
            let sana = today.getDate()
            let oy = OyNomlari[today.getMonth()]

            return `${soat}:${minut} - ${haftaKuni}, ${sana} ${oy}`
        },
        updateTime() {
            this.time = this.now()
        }
    },
    mounted() {
        this.updateTime()
        setInterval(this.updateTime, 60000)

    }
}
</script>

<style></style>
