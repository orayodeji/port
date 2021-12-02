<template>
    <a :href="projectLink" target="_blank" rel="noreferrer noopener" class="portfolio__project--col portfolio__project" :data-mobile-num="mobileNum" :data-desktop-num="desktopNum" style="color: #fff; text-decoration: none;">
        <div class="portfolio__project-item" :style="{ width: containerWidth }">
            <div class="portfolio__project-image" :style="[ computedHeight ? '' : {height} ,{ width: containerWidth }]" @click="open">
                <!-- https://images.pexels.com/photos/8817870/pexels-photo-8817870.jpeg?auto=compress&cs=tinysrgb&dpr=1&w=500 -->
                <img data-scroll data-scroll-speed="1" :style="[ computedHeight ? '' : {height} ,{ width: containerWidth }]" :src="projectImage" alt="">
            </div>
            <div class="portfolio__project-info" data-scroll data-scroll-speed="0.7">
                <div class="portfolio__project-title">
                    <h4 class="portfolio__project-name">{{projectTitle}}</h4>
                    <p class="portfolio__project-tags" v-html="projectTags"></p>
                </div>
                <a :href="projectLink" class="arrow-bg" target="_blank" rel="noreferrer noopener"></a>
            </div>
        </div>
    </a>
</template>

<script>
export default {
    props: {
        maxWidth: {
            // The default maxiumum width is 100%.
            default: 100,
            type: Number,
        },
        minWidth: {
            // Lines have a minimum width of 80%.
            default: 80,
            type: Number,
        },
        height: {
            // Make lines the same height as text.
            default: '1em',
            type: String,
        },
        width: {
            // Make it possible to define a fixed
            // width instead of using a random one.
            default: null,
            type: String,
        },
        containerWidth: {
            default: null,
            type: String
        },
        mobileNum: String,
        desktopNum: String,
        projectTitle: String,
        projectTags: String,
        projectImage: {
            default: 'https://images.pexels.com/photos/8817870/pexels-photo-8817870.jpeg?auto=compress&cs=tinysrgb&dpr=1&w=500',
            type: String,
        },
        projectId: Number,
        projectLink: String
    },
     computed: {
        computedWidth() {
            // Either use the given fixed width or
            // a random width between the given min
            // and max values.
            return this.width || `${Math.floor((Math.random() * (this.maxWidth - this.minWidth)) + this.minWidth)}%`;
        },
        computedHeight() {
            if (this.projectId === 1 || this.projectId === 3
                    || this.projectId === 5 || this.projectId === 6 
                        || this.projectId === 7 || this.projectId === 8) {
                            return true
            } 

            return false
        }
    },
    methods: {
        open() {
            this.$emit('open')
        }
    }
}
</script>