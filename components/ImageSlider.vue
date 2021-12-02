<template>
    <div class="imageSlider">
        <SliderItem :image="prevImage" />
        <SliderItem :image="currentImage" :active="activeAnimation" />
    </div>
</template>

<script>
export default {
    props: {
        imagesData: Array
    },
    data() {
        return {
            activeAnimation: true,
            activeSliderIndex: 0,
            timer: null,
        }
    },
    computed: {
        prevImage() {
            return (this.imagesData[this.activeSliderIndex - 1] ||
                this.imagesData[this.imagesData?.length - 1]
            )
        },
        currentImage() {
            return this.imagesData[this.activeSliderIndex]
        }
    },
    created() {
        this.timer = setInterval(() => {
            this.goToNext();
        }, 6000);
    },
    methods: {
        goToNext() {
            this.activeAnimation = !this.activeAnimation
            setTimeout(() => {
                this.activeAnimation = !this.activeAnimation
                this.activeSliderIndex = this.activeSliderIndex >= this.imagesData.length - 1 ? 0 : this.activeSliderIndex + 1
            }, 500);
        }
    },
    beforeDestroy() {
        clearInterval(this.timer)
    }
}
</script>