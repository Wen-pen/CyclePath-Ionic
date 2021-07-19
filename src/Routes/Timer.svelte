<script>
    import {onMount} from "svelte"
    import {Motion} from "@capacitor/motion"
    import {Storage} from "@capacitor/storage"
    let time =  {statName: "Time", stat: 0, unit: "s" }
    let speed = {statName: "Speed", stat: 0, unit: "KMH"}
    let dist =  {statName: "Distance", stat: 0, unit: "KM"}
    let speedList = []
    let distance = 0
       
    export let statList = [time, speed, dist]

    const start = Date.now()
    setInterval(() => {
        const millis = Date.now() - start;
        let secs = Math.floor(millis / 1000)
        time.stat = secs
        time = time
        statList = statList
    },1000);

    let speedCheck = setInterval(() => {
        speedList.push(speed.stat)
        speedList = speedList
        console.log(speedList)
    }, 10000)


    onMount(async () => {
        Motion.addListener('accel', (event) => {
            let velx = 0 + event.acceleration.x * time.stat
            let vely = 0 + event.acceleration.y * time.stat
            let velz = 0 +  event.acceleration.z * time.stat
        
            let vel = (velx + vely + velz) / 3
            if (Math.floor(vel) < 0){
                vel = vel * -1
            }

            speed.stat = Math.floor(vel)
            speed = speed
            statList = statList
        })
    })

    
    let saveStats = async () => {
        clearInterval(speedCheck)
        for(let sped in speedList){
            distance = distance + (Number(sped) * time.stat)
        }
        dist = dist.stat
        dist = dist
        statList = statList

        await Storage.set({
            key: 'lastTime',
            value: time.stat
        })

       await Storage.set({
            key: 'lastSpeed',
            value: speed.stat
        })

        await Storage.set({
            key: 'lastDist',
            value: dist.stat
        })
    }
</script>

    <ion-content>
        {#each statList as {statName, stat, unit}}
            <h3 class="title">
                {statName}:
            </h3>
            <h4>
                {stat} {unit}
            </h4>
            <br>
        {/each}
        <ion-grid>
            <ion-row>
                <ion-button href="/" on:click={saveStats}>
                    Stop
                </ion-button>
            </ion-row>
        </ion-grid>
    </ion-content>

<style>
*{
    margin: 10px;
    display: flex;
    align-items: center;
    justify-content: space-around ;
}

ion-button{
    --background: #CD8B79;
    width: 139px;
    height: 44px;
  }
</style>