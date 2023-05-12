<script>
  import { onMount } from 'svelte';
   // Dimensions
   const width = 800;
   const height = 100;
   const margin = { top: 10, right: 20, bottom: 20, left: 20 };
   const innerWidth = width - margin.left - margin.right;
   const innerHeight = height - margin.top - margin.bottom;
 
   // Arrays
   const points = [
     innerWidth / 2 - 60,
     innerWidth / 2 - 30,
     innerWidth / 2,
     innerWidth / 2 + 30,
     innerWidth / 2 + 60
   ];
 
   // All lights with a higher index are on!
   let index = points.length;
 
   // Color
   let color = "darkred";

    // Function to reduce index by 1 every second
    const countdown = () => {
   if (index === 0) {
     color = "darkgreen";
     clearInterval(interval);
   } else {
     index -= 1;
     color = "darkred";
   }
 };
   let interval;
     // Set interval to call countdown function every second
   function startCountdown() {
     interval = setInterval(countdown, 1000);
   }

   onMount(() => {
     startCountdown();
   });

 </script>
 
 <svg viewBox="0 0 {width} {height}">
   <g transform="translate({margin.left},{margin.top})">
     {#each points as point, i}
       <circle
       cx={point}
       cy={innerHeight/2}
       r="10"
       fill={i >= index ? color : "rgba(0, 0, 0, 0.3)"}
     />
     {/each}
   </g>
 </svg>
 