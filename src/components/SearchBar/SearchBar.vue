<template>
    <div class="search-box">
        <div class="search-input-box">
            <input type="text" id="search-input" class="search-input" placeholder="Joyni qidirish..." v-model="city"
                @keydown.enter="sendCity">
            <label for="search-input">
                <i class='bx bx-search'></i>
            </label>
        </div>
        <div>
            <p class="text-3.5 text-white font-normal">Ob-havo ma'lumotlari...</p>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            city: ''
        }
    },
    methods: {
        sendCity() {
            this.$emit('SearchCity', this.city)
        }
    },
}
</script>

<style>
.search-box {
    padding-top: 40px;
}

.search-input-box {
    width: 370px;
    height: 50px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    border-bottom: 2px solid #a3a0a0;
    margin-bottom: 40px;
}

.search-input {
    width: 70%;
    height: 100%;
    border: none;
    outline: none;
    color: rgb(255, 255, 255, 0.7);
}

.bx-search {
    color: #fff;
    font-size: 28px;
    margin-right: 10px;
}
</style>