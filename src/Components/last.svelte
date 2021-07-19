<script>
    export let speed
    export let distance
    export let time
</script>

<ion-col>
    <ion-row>
      <div class="maddening">
        {speed} M/s
     </div>
      <ion-row>
        <div class="maddening">
          {distance} KM
       </div>
       <ion-row>
      <div class="maddening">
        {time}s
     </div>
      </ion-row>
        </ion-row>
  </ion-col>
<style>
  ion-row{
    justify-content: center;
  }
  .maddening{
    padding: 10px
  }
</style>
  