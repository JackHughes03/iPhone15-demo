<script setup>
import { ref, onMounted } from 'vue';

const notch = () => {
    const notch = document.querySelector('.notch-notexpanded');
    notch.classList.toggle('notch-expanded');
    
    if (notch.classList.contains('notch-expanded')) {
        notch.classList.remove('hover:scale-110');
    } else {
        notch.classList.add('hover:scale-110');
    }
}

const charge = () => {
    const phone = document.querySelector('.phone'),
    standby = document.querySelector('.standby'),
    time = document.querySelector('.time');
    
    phone.classList.toggle('chargeme');
    
    setTimeout(() => {
        phone.classList.remove('phone');
        standby.classList.add('opacity-100');
        time.classList.toggle('hidden');
    }, 1000);
}

const music = () => {
}
</script>

<template>
    <div id="app" class="h-full w-full">
        <aside>
            <button class="bg-[#3859d1] text-black font-semibold px-8 rounded mt-2 py-2 ml-2 text-xl" @click="charge">Charge me</button>
            <button class="bg-[#3859d1] text-black font-semibold px-8 rounded mt-2 py-2 ml-2 text-xl" @click="music">Play music</button>
        </aside>
        
        <main class="flex justify-center absolute bottom-10 w-full">
            <section class="phone border-[10px] cursor-pointer border-black outline outline-[#ffc7ee7c] h-[720px] w-[350px] bg-black rounded-[53px] duration-300">
                <section @click="notch" class="w-[100px] notch-notexpanded h-[30px] z-10 rounded-full mt-2 bg-black absolute left-1/2 cursor-pointer -translate-x-1/2 duration-300 hover:scale-110">
                    <div class="w-1 outline outline-[#04071f] h-1 absolute right-[12px] rounded-full top-[12px]"></div>
                </section>
                
                <section class="flex flex-col items-center justify-center mt-16 text-white opacity-70 time">
                    <p class="text-lg">Monday, June 5</p>
                    <p class="text-[80px] -mt-5">9:41</p>
                    
                    <p class="absolute bottom-6 text-[10px] swipeup">Swipe up to unlock</p>
                    <hr class="w-[110px] border-2 rounded absolute bottom-4 homebar">
                </section>
                
                <section class="standby duration-700 opacity-0 w-full h-full flex justify-center z-0 items-center">
                    <div class="rotate-[-90deg] flex font-black text-[270px] text-white">
                        <p class="text-pink-400 opacity-70">9</p>
                        <p class="-m-8 text-gray-500 opacity-70">:</p>
                        <p class="rotate-6 text-purple-400 opacity-70">4</p>
                        <p class="-rotate-6 -ml-10 text-purple-950 opacity-70">1</p>
                    </div>
                </section>
            </section>
        </main>
    </div>
</template>

<style lang="postcss">
@import url('https://fonts.googleapis.com/css2?family=Varela+Round&display=swap');

@font-face {
    font-family: 'SF Pro Display';
    src: url('/src/assets/fonts/medium.otf');
}

.notch-expanded {
    @apply w-[39%] h-16;
}

.phone {
    background-image: url('/src/assets/images/iphone.png');
    background-repeat: no-repeat;
    background-size: cover;
}

.chargeme {
    animation: animate-charge 1s forwards;
}

.standby {
    font-family: Varela Round;
}

.time {
    font-family: 'SF Pro Display';
}

.homebar {
    animation: jump 5s infinite;
}

.swipeup {
    animation: swipe 4s forwards;
}

@keyframes animate-charge {
    0% {
        transform: rotate(0deg);
    }
    100% {
        transform: rotate(90deg);
    }
}

@keyframes jump {
    0% {
        transform: translateY(-2px);
    }
    50% {
        transform: translateY(-10px);
    }
    100% {
        transform: translateY(-2px);
    }
}

@keyframes swipe {
    0% {
        transform: translateY(0px);
    }
    50% {
        transform: translateY(-8px);
    }
    100% {
        opacity: 0;
    }
}

</style>