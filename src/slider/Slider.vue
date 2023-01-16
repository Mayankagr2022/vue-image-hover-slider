<template>
    <div class="main-container">
        <div class="container">
            <img v-for="(image,index) in images" v-bind:src="image" v-if="index===currentIndex" @mouseenter="imgHover"  />
        </div>
        <div class="indicator-container">
                <span v-for="(image,index) in images" v-bind:class="{ active: (image,index) === currentIndex }"
                    @mouseenter="currentIndex = index"></span>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            images: [
                'https://i.postimg.cc/QNYkPnvr/p1.jpg',
                'https://i.postimg.cc/W1B5yfF4/p2.jpg',
                'https://i.postimg.cc/h40PPkcH/p4.jpg',
            ],
            currentIndex:0,
            // imgHover:false,
        }
    },
    methods: {
        imgHover(){
            setInterval(()=>{
                this.currentIndex = (this.currentIndex + 1 + this.images.length) % this.images.length;
            },1000)
        },

    },
}
</script>

<style scoped>
.main-container{
    margin: auto;
    margin-top: 250px;
    margin-left:200px ;
    position: relative;
}
.container{
    width: 320px;
    height: 522px;
}
img {
    position: absolute;
    width: 320px;
    height: 522px;
}
.indicator-container {
    width: 320px;
    height: 3px;
    display: flex;
}
.indicator-container span {
    width: 100%;
    height: 3px;
}
 span.active {
    transition: 0.3s ease-in;
    width: 100%;
    height: 3px;
    background-color: black;
    opacity: 1;
}
</style>
