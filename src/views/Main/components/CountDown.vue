<template>
    <section class="container my-24">
        <div class="bg-black flex justify-between h-[500px]">
            <div class=" w-[42%] pt-[58px] pl-16 pb-[45px] flex flex-col gap-5 items-start">
                <p class="text-[#00FF66]">Categories</p>
                <div class=" text-[#fafafa] font-inter font-bold text-[48px]  my-2">
                    Enhance Your Music Experience
                </div>
                <div class="flex w-[320px] justify-between items-center">
                    <div class="flex flex-col-reverse items-center justify-center h-16 w-16 rounded-full bg-white ">
                        <p class=" text-xs font-medium font-poppins">Days</p>
                        <span class=" font-semibold font-inter">{{ time?.days }}</span>
                    </div>
                    <div class="flex flex-col-reverse items-center justify-center h-16 w-16 rounded-full bg-white">
                        <p class=" text-xs font-medium font-poppins">Hours</p>
                        <span class=" font-semibold font-inter">{{ time?.hours }}</span>
                    </div>
                    <div class="flex flex-col-reverse items-center justify-center h-16 w-16 rounded-full bg-white">
                        <p class=" text-xs font-medium font-poppins">Minutes</p>
                        <span class=" font-semibold font-inter">{{ time?.minutes }}</span>
                    </div>
                    <div class="flex flex-col-reverse items-center justify-center h-16 w-16 rounded-full bg-white">
                        <p class=" text-xs font-medium font-poppins">Seconds</p>
                        <span class=" font-semibold font-inter">{{ time?.seconds }}</span>
                    </div>
                </div>
                <button class=" py-4 px-12 bg-[#00FF66] rounded text-base font-medium font-poppins text-[#fafafa]">Buy
                    Now!</button>
            </div>
            <div class=" w-[55%] overflow-hidden  h-full flex items-center justify-center bg-[radial-gradient(ellipse_at_center,_var(--tw-gradient-stops))] from-[#D9D9D9] bg-opacity-30 from-0% to-black to-70%">
                <img class=" object-cover object-center  " src="@/assets/img/bombox.svg" alt="">
            </div>
        </div>

    </section>
</template>

<script setup>
import { onMounted, ref } from "vue";

onMounted(() => {
    updateCountdown();
    setInterval(updateCountdown, 1000);
}
)
let time = ref({
    days: '00',
    hours: '00',
    minutes: '00',
    seconds: '00'
})



const updateCountdown = () => {
    const targetDate = new Date('2024-07-20T00:00:00');
    const now = new Date();
    const difference = targetDate - now;
    time.value.days = String(Math.floor(difference / (1000 * 60 * 60 * 24))).padStart(2, '0');
    time.value.hours = String(Math.floor((difference % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60))).padStart(2, '0');
    time.value.minutes = String(Math.floor((difference % (1000 * 60 * 60)) / (1000 * 60))).padStart(2, '0');
    time.value.seconds = String(Math.floor((difference % (1000 * 60)) / 1000)).padStart(2, '0');
}

</script>
