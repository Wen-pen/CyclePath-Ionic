<ion-app>
  <ion-content fullscreen>
    <ion-grid>
      <ion-col>
        <div class="img-container">
          <img src="logo.svg" alt="Cyclepath Logo"/>
        </div>
      </ion-col>
      <ion-col>
        <h2>CyclePath</h2>
      </ion-col>
    </ion-grid>
    <ion-grid class="your-mother">
      <ion-button href="/start" class="justify-content-center">
        Start
      </ion-button>
    </ion-grid>
    <ion-grid class="your-mother">
      <ion-button href="/last" class="justify-content-center">
        Load Last Times
      </ion-button>
    </ion-grid>
  </ion-content>
</ion-app>

<style lang="css">

  .img-container {
    display: flex;
    align-items: center;
    justify-content: center;
  }

  img {
    height: 300px;
    width: 300px;
  }

  h2 {
    margin-top: 50px;
    text-align: center;
  }

  :root{
		--ion-font-family: Nunito,sans-serif;
    text-align:center;
   --ion-background-color: #ABD1B5;
  }

  ion-content{
    --background: url(../overlay.jpg) no-repeat left top
  }
  ion-button{
    --background: #CD8B79;
    width: 139px;
    height: 44px;
    margin-top: 75px;
  }
</style>
