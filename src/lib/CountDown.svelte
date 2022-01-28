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

<div class="flex flex-col justify-between text-center items-stretch font-sans font-bold md:flex-row md:justify-evenly">
    <div class="pt-5 md:w-40">
      <h3 class="text-4xl md:text-7xl">
        {zero_padding(time_remainig.days)}
      </h3>
      <h4 class="text-xl md:text-3xl">
        {#if time_remainig.days == 1}
          día
        {:else}
          días
        {/if}
      </h4>
    </div>
    <div class="pt-5 md:w-40">
      <h3 class="text-4xl md:text-7xl">
        {zero_padding(time_remainig.hours)}
      </h3>
      <h4 class="text-xl md:text-3xl">
        {#if time_remainig.hours == 1}
          hora
        {:else}
          horas
        {/if}
      </h4>
    </div>
    <div class="pt-5 md:w-40">
      <h3 class="text-4xl md:text-7xl">
        {zero_padding(time_remainig.minutes)}
      </h3>
      <h4 class="text-xl md:text-3xl">
        {#if time_remainig.minutes == 1}
          minuto
        {:else}
          minutos
        {/if}
      </h4>
    </div>
    <div class="pt-5 md:w-40">
      <h3 class="text-4xl md:text-7xl">
        {zero_padding(time_remainig.seconds)}
      </h3>
      <h4 class="text-xl md:text-3xl">
        {#if time_remainig.seconds == 1}
          segundo
        {:else}
          segundos
        {/if}
      </h4>
    </div>
</div>
