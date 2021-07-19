<script>
import { onMount } from "svelte";
import { Storage } from "@capacitor/storage"
import Last from "../Components/last.svelte";


let statList = {
    speed: null, 
    time: null,
    distance: null
}
    onMount(
     async () => {
        let speed =  await Storage.get({key: 'lastSpeed'})
        let time =  await Storage.get({key: 'lastTime'})
        let dist =  await Storage.get({key: 'lastDist'})

       statList.speed = speed.value
       statList.time = time.value
       
       if (!statList.distance)
            statList.distance = 0
        else
            statList.distance = dist.value

       statList = statList
     }
    )
</script>


<Last {...statList}/>
<ion-button href="/">
    Back
</ion-button>

<style>
ion-button{
    --background: #CD8B79;
    width: 139px;
    height: 44px;
    margin-top: 75px;
  }
</style>
