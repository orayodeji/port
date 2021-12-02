<template>
    <transition name="modal-slidein" mode="out-in">
        <div class="portfolio__modal--backdrop" :class="[active ? 'fade': '']">
            <div class="modal overflow-auto"
                style="display: block"
                role="dialog"
                aria-labelledby="modalTitle"
                aria-describedby="modalDescription"
            >
                <div class="modal-dialog">
                    <div class="modal-dialog__">
                        <div class="modal-dialog__content">
                            <div class="modal-dialog__header">
                                <div class="modal-dialog__header__">
                                    <div>
                                        <slot name="title">
                                            <h5 class="modal-dialog__title">Modal Title</h5>
                                            <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Similique, illum?</p>
                                        </slot>
                                    </div>
                                    <div class="btn btn-icon btn-sm btn-active-icon-primary close" @click="close">
                                        <span class="svg-icon svg-icon-2x">
                                            <svg xmlns="http://www.w3.org/2000/svg" width="30" height="30" viewBox="0 0 24 24" fill="none">
                                                <path
                                                    opacity="0.25"
                                                    fill-rule="evenodd"
                                                    clip-rule="evenodd"
                                                    d="M2.36899 6.54184C2.65912 4.34504 4.34504 2.65912 6.54184 2.36899C8.05208 2.16953 9.94127 2 12 2C14.0587 2 15.9479 2.16953 17.4582 2.36899C19.655 2.65912 21.3409 4.34504 21.631 6.54184C21.8305 8.05208 22 9.94127 22 12C22 14.0587 21.8305 15.9479 21.631 17.4582C21.3409 19.655 19.655 21.3409 17.4582 21.631C15.9479 21.8305 14.0587 22 12 22C9.94127 22 8.05208 21.8305 6.54184 21.631C4.34504 21.3409 2.65912 19.655 2.36899 17.4582C2.16953 15.9479 2 14.0587 2 12C2 9.94127 2.16953 8.05208 2.36899 6.54184Z"
                                                    fill="#12131A"
                                                ></path>
                                                <path
                                                    fill-rule="evenodd"
                                                    clip-rule="evenodd"
                                                    d="M8.29289 8.29289C8.68342 7.90237 9.31658 7.90237 9.70711 8.29289L12 10.5858L14.2929 8.29289C14.6834 7.90237 15.3166 7.90237 15.7071 8.29289C16.0976 8.68342 16.0976 9.31658 15.7071 9.70711L13.4142 12L15.7071 14.2929C16.0976 14.6834 16.0976 15.3166 15.7071 15.7071C15.3166 16.0976 14.6834 16.0976 14.2929 15.7071L12 13.4142L9.70711 15.7071C9.31658 16.0976 8.68342 16.0976 8.29289 15.7071C7.90237 15.3166 7.90237 14.6834 8.29289 14.2929L10.5858 12L8.29289 9.70711C7.90237 9.31658 7.90237 8.68342 8.29289 8.29289Z"
                                                    fill="#12131A"
                                                ></path>
                                            </svg>
                                        </span>
                                    </div>
                                </div>
                            </div>
                            <div class="modal-dialog__body">
                                <div class="modal-dialog__tech-stack__">
                                    <p>TECH</p>
                                    <div class="modal-dialog__tech-stacks">   
                                        <div class="modal-dialog__tech-stacks__">
                                            <slot name="stack" />
                                        </div>
                                    </div>
                                </div>
                                <div>
                                    <div class="slider-main">
                                        <div class="slider" :class="[active ? 'active': '']">
                                            <div class="slider-inner">
                                                <slot name="sliders" />
                                            </div>
                                        </div>
                                    </div>
                                </div>
                                <div class="slider-description">
                                    <slot name="description" />
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </transition>
</template>

<script>
export default {
    data() {
        return {
            
        }
    },
    props: {
        active: Boolean
    },
    methods: {
        close() {
            this.$emit('close')
        },
        slider() {
            let slider = document.querySelector('.slider');
            let innerSlider = document.querySelector('.slider-inner');

            // Create useful variables
            let pressed = false;
            let startx;
            let x;

            /**
             * Add multiple event listeners
             */
            if(slider) {
                // Enable dragging aross the slider when user clicks/drag across
                slider.addEventListener('mousedown', (e) => {
                    pressed = true; // slider has been clicked/grabbed
                    startx = e.offsetX - innerSlider.offsetLeft; // Gives the number of how many px the left-hand side of the slider is to the parent `.slider`
                    slider.style.cursor = 'grabbing';
                })

                // Change cursor on hover of the slider items
                slider.addEventListener('mouseenter', (e) => {
                    slider.style.cursor = 'grab';
                })

                // Change cursor when not hovering on the slider items
                // slider.addEventListener('mouseleave', (e) => {
                //     slider.style.cursor = 'default';
                // })

                // Set the cursor back to grab again
                slider.addEventListener('mouseup', (e) => {
                    slider.style.cursor = 'grab';
                })

                // Add general event listener. When the mouse is not pressed set pressed to false
                window.addEventListener('mouseup', (e) => {
                    pressed = false;
                })

                slider.addEventListener('mousemove', (e) => {
                    if(!pressed) return; // If pressed isn't true return nothing
                    e.preventDefault(); // Enable dragging along slider and disable other pointer events

                    x = e.offsetX;

                    innerSlider.style.left = `${x - startx}px`;

                    checkBoundary()
                })
            }
            // Check boundary when slider item touches parent scope
            function checkBoundary() {
                let outer = slider.getBoundingClientRect()
                let inner = innerSlider.getBoundingClientRect()

                if(parseInt(innerSlider.style.left) > 0) {
                    innerSlider.style.left = '30px';
                } else if (inner.right < outer.right) {
                    innerSlider.style.left = `-${inner.width - outer.width}px`;
                }
            }
        }
    },
    mounted() {
        this.slider()
    }
  }
</script>

<style scoped>
.modal-slidein-enter-active,
.modal-slidein-leave-active {
    transition: transform .5s ease
}

.modal-slidein-enter,
.modal-slidein-leave-active {
    transform: translateY(100%);
}
</style>