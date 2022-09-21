<template>
    <div class="music">
        <audio id="audio">
            <source type="audio/mpeg" src="">
        </audio>
        
        <button class="music-ico"><i id="previous" class='bx bx-skip-previous'></i></button> 
        <button class="music-ico"><i id="play" class='bx bx-play'></i></button>
        <button class="music-ico"><i id="next" class='bx bx-skip-next' ></i></button>
        
    </div>
</template>

<style lang="scss" scoped>
.music{
    text-align: center;
}
.music-ico {
    display: inline-block;
    box-sizing: border-box;
    color: black;
    border: none;
    width: 25px;
    height: 25px;
    border-radius: 20px;
    padding: 0;
    margin: 2px;
    cursor: pointer;
    & i{
        text-align: center;
        vertical-align: middle;
        font-size: 20px;
    }
}
</style>
<script>
import $ from 'jquery'

$(function(){
    var audio = $("#audio")[0],
        play  = $("#play"),
        previous = $("#previous"),
        next = $("#next"),
        num = 0;

    var music123 = ["https://drive.google.com/uc?export=download&id=1nnKDEBzdGHEPbplooAtRQLA_rkhMlW0n",
                    "https://drive.google.com/uc?export=download&id=1auDWY7x-Lza0hBbiLLIKNxY605kfX-Rk",
                    "https://drive.google.com/uc?export=download&id=1EXMxMyXlcDiM0kWVB2Jz82pe9KLSAxx7",
                    "https://drive.google.com/uc?export=download&id=1i1Q6NydQmZebmX2-EEVtcH2jTuV0Bh31",
                    "https://drive.google.com/uc?export=download&id=1eEgCvnQdVKqmNCWXyGnq_KSMOILkFN0T"];

    play.click(function(){
        if(audio.paused){
            audio.play();
            play.attr("class" , "bx bx-pause");
        }
        else if(audio.played){
            audio.pause();
            play.attr("class" , "bx bx-play");
        }
    });
    previous.click(function(){
        if(num > 0){
            audio.src = music123[num-1];
            audio.play();
            play.attr("class" , "bx bx-pause");
            num--;
        }
        else{
            num = 4;
        }
    });
    next.click(function(){
        if(num < 4){
            audio.src = music123[num+1];
            audio.play();
            play.attr("class" , "bx bx-pause");
            num++;
        }
        else{
            num = 0;
        }
    });
});
</script>