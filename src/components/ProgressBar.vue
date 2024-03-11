<template>
    <div class="specs">
        <div class="progress-bar">
            <div class="progress-circle">
                <div class="progress-content">
                    <h2 class="progText">{{ count }}%</h2>
                </div>
                <div class="progress">
                    :style="{
                        transition:50 * data.progress[slideIndex] + 'ms',
                        bottom: + data.progress[slideIndex] -110 + '%'
                    }"
                </div>
            </div>
        </div>
        <small>Durability<b></b></small>
    </div>
</template>

<script>

export default {
    name: 'ProgressBar',
    props: {
        data: Object,
        count: Number,
        slideIndex: Number,
    }    
}
</script>

<style scoped>
.specs {
    padding-left: 2em;
    text-align: center;
}
.progress-bar{
    margin-bottom: 0.5em;
}
.progress-circle {
    position: relative;
    background: transparent;
    border: #17374b *px solid;
    width: 7em;
    height: 7em;
    border-radius:100%;
    overflow: hidden;
}
.progress {
width: 7em;
height: 7em;
position: absolute;
left: 50%;
transform: translateX(-50%);
bottom: 100%; 
background: linear-gradient( 0deg, #1ba7a1, #12c141 );
transition: bottom 4.5s;
}
.progress-content {
background: #204430;
width: 5.5em;
height: 5.5em;
position: absolute;
top: 50%;
left: 50%;
transform: translate(-50%,-50%);
border-radius: 100%;
display: flex;
align-items: center;
justify-content: center;
color: #fff;
z-index: 1;
}
@media screen and(max-width:880px){
    .specs{
        padding-left: 0;
    }
}
</style>