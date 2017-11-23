<template>
    <div v-if="Platform.is.win" style="position: fixed; bottom: 8px; left:0; right:0; margin: auto;"
         id='winAd'>
    </div>
</template>

<script>
import { Utils, Platform, Dialog } from 'quasar'
export default {
    beforeCreate() {
        console.log("beforeCreate")
    },
    mounted() {

//android
        if (Platform.is.android) {

            if (AdMob) AdMob.createBanner({
                adId: "ca-app-pub-3940256099942544/6300978111" , //test value
                position: AdMob.AD_POSITION.BOTTOM_CENTER,
                autoShow: true
            });
        }
//windows
        if (Platform.is.win) {


            this.adLoaded = true;
            var adContainer = document.getElementById("winAd")
            var adId=''
            var adUnit=''
            if(Platform.is.mobile){
            adContainer.style.width = '300px';
            adContainer.style.height = '50px';
            }else{
            adContainer.style.width = '728px';
            adContainer.style.height = '90px';
            }
            //add on head //Microsoft.Advertising.JavaScript/ad.js

            var ad = new MicrosoftNSJS.Advertising.AdControl(adContainer, {
                applicationId: '3f83fe91-d6be-434d-a0ae-7351c5a997f1',
                adUnitId: 'test'
            })
        }
    }
}
</script>
