<template>
<div class="block">
    <div>
        <p class="digit">{{ days | two_digits }}</p>
        <div class="text">Days</div>
    </div>

    <div>
        <p class="digit">{{ hours | two_digits }}</p>
        <p class="text">Hours</p>
    </div>

    <div>
        <p class="digit">{{ minutes | two_digits }}</p>
        <p class="text">Minutes</p>
    </div>

    <div>
        <p class="digit">{{ seconds | two_digits }}</p>
        <p class="text">Seconds</p>
    </div>
</div>
</template>

<script>
export default {
    name: 'countdown',
    mounted: function() {
        window.setInterval(() => {
            this.now = Math.trunc((new Date()).getTime() / 1000);
        },1000);
    },
    props : {
        date : {
            type: Number        
        }
    },
    data() {
        return {
            now: Math.trunc((new Date()).getTime() / 1000)
        }
    },
    computed: {
        inputDate: function() {
            return Math.trunc(Date.parse(this.date) / 1000);
        }, 
        seconds() {
            return (this.inputDate - this.now) % 60;
        },
        minutes() {
            return Math.trunc((this.inputDate - this.now) / 60) % 60;
        },
        hours() {
            return Math.trunc((this.inputDate - this.now) / 60 / 60) % 24;
        },
        days() {
            return Math.trunc((this.inputDate - this.now) / 60 / 60 / 24);
        }
    }
}
</script>

<style>
@import url(https://fonts.googleapis.com/css?family=Roboto+Condensed:400|Roboto:100);
.block {
    display: inline-block;
    text-align: center;
}

.block > div {
    padding: 100px;
    border-radius: 3px;
    display: inline-block;
    text-align: center;
}

.text {
    color: #1abc9c;
    font-size: 40px;
    font-family: 'Roboto Condensed', serif;
    font-weight: 400;
}

.digit {
    color: #000000;
    font-size: 150px;
    font-weight: 100;
    font-family: 'Roboto', serif;
    margin: 10px;
    text-align: center;
}

</style>