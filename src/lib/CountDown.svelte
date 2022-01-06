<script>
  import { intervalToDuration } from "date-fns";
  const target_date = new Date(2022, 2, 5, 16);

  function zero_padding(num){
    return num>0 && num<10 ? `0${num}` : `${num}`
  }

  function get_duration() {
    const duration = intervalToDuration({
      start: target_date,
      end: new Date(),
    });
    return {
      days: duration.days,
      hours: duration.hours,
      minutes: duration.minutes,
      seconds: duration.seconds,
    };
  }

  let time_remainig = get_duration();
  setInterval(() => {
    time_remainig = get_duration();
  }, 1000);
</script>

<div class="font-extrabold text-white flex flex-col justify-center mt-10 xl:mt-20">
  <!-- <h1 class="mb-3 text-center text-2xl xl:text-6xl">¿Cuánto falta para el festival?</h1> -->
  <div class="flex justify-center text-xl xl:text-4xl mt-5 xl:mt-10">
    <div class="flex flex-col items-center justify-center mx-2 xl:mx-5">
      <h3 class="xl:text-6xl">
        {zero_padding(time_remainig.days)}
      </h3>
      <h4 class="xl:mt-2">
        {#if time_remainig.days == 1}
          día
        {:else}
          días
        {/if}
      </h4>
    </div>
    <div class="flex flex-col items-center justify-center mx-2 xl:mx-5">
      <h3 class="xl:text-6xl">
        {zero_padding(time_remainig.hours)}
      </h3>
      <h4 class="xl:mt-2">
        {#if time_remainig.hours == 1}
          hora
        {:else}
          horas
        {/if}
      </h4>
    </div>
    <div class="flex flex-col items-center justify-center  mx-2 xl:mx-5">
      <h3 class="xl:text-6xl">
        {zero_padding(time_remainig.minutes)}
      </h3>
      <h4 class="xl:mt-2">
        {#if time_remainig.minutes == 1}
          minuto
        {:else}
          minutos
        {/if}
      </h4>
    </div>
    <div class="flex flex-col items-center justify-center  mx-2 xl:mx-5">
      <h3 class="xl:text-6xl">
        {zero_padding(time_remainig.seconds)}
      </h3>
      <h4 class="xl:mt-2">
        {#if time_remainig.seconds == 1}
          segundo
        {:else}
          segundos
        {/if}
      </h4>
    </div>
  </div>
</div>
