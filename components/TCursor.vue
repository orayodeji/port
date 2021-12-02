<template>
    <div class="cursor" :class="[{'hovermenu': isHoveringOnButton}, {'hoverproject': isHoveringOnProject}]">
        <span class="cursor__cta">Learn More</span>
        <span class="cursor__menu">menu</span>
        <span class="cursor__discover">View Project</span>
        <svg width="26" height="14" viewBox="0 0 26 14" fill="none" xmlns="http://www.w3.org/2000/svg">
            <g clip-path="url(#arrow)">
                <path d="M1 6.8999H25" stroke-width="2" stroke-miterlimit="10" stroke-linecap="round" stroke-linejoin="round"></path>
                <path d="M19.1001 1L25.0001 6.9L19.1001 12.8" stroke-width="2" stroke-miterlimit="10" stroke-linecap="round" stroke-linejoin="round"></path>
            </g>
            <defs>
                <clipPath id="arrow">
                    <rect width="26" height="13.8" fill="white"></rect>
                </clipPath>
            </defs>
        </svg>
    </div>
</template>

<script>
export default {
	data() {
        return {
            isHoveringOnButton: false,
            isHoveringOnProject: false,
        }
    },
	mounted(){
        window.addEventListener("load", this.initCursor())
    },
    methods:{
        initCursor(){
            const w = document.querySelector("main");
            const buttons = w.querySelectorAll(".portfolio__menu")
            const projects = w.querySelectorAll(".portfolio__project")

            // Hover on button
            buttons.forEach((button) =>{
                button.addEventListener("mouseover", () => {
                    console.log('mouse enter triggered')
                    this.isHoveringOnButton = true
                })

                button.addEventListener("mouseout", () => {
                    this.isHoveringOnButton = false
                })
            })

            // Hover on projects
            projects.forEach((project) =>{
                project.addEventListener("mouseover", () => {
                    console.log('mouse enter triggered')
                    this.isHoveringOnProject = true
                })

                project.addEventListener("mouseout", () => {
                    this.isHoveringOnProject = false
                })
            })
        }
    }
}
</script>

<style scoped>
/* .cursor {
	display: none;
} */

@media (any-pointer: fine) {
	/* .cursor {
		position: fixed;
		top: 0;
		left: 0;
		display: block;
		pointer-events: none;
	}
	.cursor__inner {
		fill: var(--cursor-fill);
		stroke: var(--cursor-stroke);
		stroke-width: var(--cursor-stroke-width);
	} */
}
.cursor {
    height: 3.5rem;
    width: 3.5rem;
    /* height: 150px;
    width: 150px; */
    position: fixed;
    z-index: 100;
    /* top: -3.2rem;
    left: -3.2rem; */
    top: 0;
    left: 0;
    pointer-events: none;
    -webkit-transition: all .9s cubic-bezier(.15,.9,.34,.95);
    -moz-transition: all .9s cubic-bezier(.15,.9,.34,.95);
    -ms-transition: all .9s cubic-bezier(.15,.9,.34,.95);
    -o-transition: all .9s cubic-bezier(.15,.9,.34,.95);
    transition: all .9s cubic-bezier(.15,.9,.34,.95);
    -webkit-transform: translate(-100px,-100px);
    -moz-transform: translate(-100px,-100px);
    -ms-transform: translate(-100px,-100px);
    -o-transform: translate(-100px,-100px);
    transform: translate(-100px,-100px);
}

.cursor__cta {
    font-style: normal;
    font-weight: 700;
    font-size: 2rem;
    line-height: 2.4rem;
    color: #231f20;
    width: 11rem;
    position: absolute;
    left: 150%;
    top: 50%;
    opacity: 0;
    -webkit-transition: all .4s cubic-bezier(.76,0,.24,1);
    -moz-transition: all .4s cubic-bezier(.76,0,.24,1);
    -ms-transition: all .4s cubic-bezier(.76,0,.24,1);
    -o-transition: all .4s cubic-bezier(.76,0,.24,1);
    transition: all .4s cubic-bezier(.76,0,.24,1);
    -webkit-transform: translate3d(2rem,-50%,0);
    -moz-transform: translate3d(2rem,-50%,0);
    -ms-transform: translate3d(2rem,-50%,0);
    -o-transform: translate3d(2rem,-50%,0);
    transform: translate3d(2rem,-50%,0);
}

.cursor__discover, .cursor__menu {
    opacity: 0;
    -webkit-transition: all .4s cubic-bezier(.15,.9,.34,.95);
    -moz-transition: all .4s cubic-bezier(.15,.9,.34,.95);
    -ms-transition: all .4s cubic-bezier(.15,.9,.34,.95);
    -o-transition: all .4s cubic-bezier(.15,.9,.34,.95);
    transition: all .4s cubic-bezier(.15,.9,.34,.95);
    font-style: normal;
    position: absolute;
    top: 50%;
    left: 50%;
    -webkit-transform: translate3d(-50%,-50%,0);
    -moz-transform: translate3d(-50%,-50%,0);
    -ms-transform: translate3d(-50%,-50%,0);
    -o-transform: translate3d(-50%,-50%,0);
    transform: translate3d(-50%,-50%,0);
}

.cursor__discover {
    font-weight: 500;
    font-size: 1.1rem;
    line-height: 1.4rem;
    letter-spacing: .1em;
    color: var(--text-color-alt);
}

.cursor__menu {
    font-weight: 500;
    font-size: 1.1rem;
    line-height: 2.4rem;
    letter-spacing: .1em;
    color: var(--text-color-alt);
}

.cursor svg {
    position: absolute;
    top: 50%;
    left: 50%;
    opacity: 0;
    -webkit-transform: translate(-50%,-50%) scale(0);
    -moz-transform: translate(-50%,-50%) scale(0);
    -ms-transform: translate(-50%,-50%) scale(0);
    -o-transform: translate(-50%,-50%) scale(0);
    transform: translate(-50%,-50%) scale(0);
    -webkit-transition: all .3s cubic-bezier(.76,0,.24,1);
    -moz-transition: all .3s cubic-bezier(.76,0,.24,1);
    -ms-transition: all .3s cubic-bezier(.76,0,.24,1);
    -o-transition: all .3s cubic-bezier(.76,0,.24,1);
    transition: all .3s cubic-bezier(.76,0,.24,1);
}

.cursor:after {
    content: "";
    display: block;
    position: absolute;
    border-radius: 50%;
    transform-origin: center;
    height: 100%;
    width: 100%;
    border: 1.5px solid var(--text-color);
    -webkit-transition: all .4s cubic-bezier(.15,.9,.34,.95);
    -moz-transition: all .4s cubic-bezier(.15,.9,.34,.95);
    -ms-transition: all .4s cubic-bezier(.15,.9,.34,.95);
    -o-transition: all .4s cubic-bezier(.15,.9,.34,.95);
    transition: all .4s cubic-bezier(.15,.9,.34,.95);
}

.cursor.hovermenu::after,
.cursor.hoverproject::after {
    background-color: var(--background-color-alt);
    border-color: var(--background-color-alt);
    border-radius: 40% 60% 54% 46%/49% 60% 40% 51%;
    -webkit-transform: scale(2);
    -moz-transform: scale(2);
    -ms-transform: scale(2);
    -o-transform: scale(2);
    transform: scale(2);
    z-index: -1;
}

.cursor.hovermenu .cursor__menu,
.cursor.hoverproject .cursor__discover {
    opacity: 1;
}
</style>