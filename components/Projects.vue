<template>
    <div>
        <project-modal v-show="isProjectModalVisible" @close="closeProjectModal" :active="isProjectModalVisible">
            <template v-slot:title v-if="projectInfo">
                <h5 class="modal-dialog__title">{{projectInfo.title}}</h5>
                <p>{{projectInfo.brief_description}}</p>
            </template>
            <template v-slot:stack v-if="projectInfo">
                <div class="tech-stack" v-for="(project_stack, index) in projectInfo.project_stacks" :key="index">
                    <span class="tech__stack--badge ">
                        {{project_stack}}
                    </span>
                </div>
            </template>
            <template v-slot:sliders>
                <div class=" modal-dialog__project-screenshot">
                    <img src="https://cdn.sanity.io/images/lcrnwy6l/production/32c5f8332be922e1225380e437296fef79c090ff-2160x1440.jpg?w=828&fit=clip" alt="" class="screeshot__img">   
                </div>
                <div class=" modal-dialog__project-screenshot">
                    <img src="https://cdn.sanity.io/images/lcrnwy6l/production/66d66ab3e44a1c800cdfdc41a91fece9f8e4e806-2160x1440.jpg?w=828&fit=clip" alt="" class="screeshot__img">
                </div>
                <div class=" modal-dialog__project-screenshot">
                    <img src="https://cdn.sanity.io/images/lcrnwy6l/production/32c5f8332be922e1225380e437296fef79c090ff-2160x1440.jpg?w=828&fit=clip" alt="" class="screeshot__img">
                </div>
                <div class=" modal-dialog__project-screenshot">
                    <img src="https://cdn.sanity.io/images/lcrnwy6l/production/66d66ab3e44a1c800cdfdc41a91fece9f8e4e806-2160x1440.jpg?w=828&fit=clip" alt="" class="screeshot__img">  
                </div>
            </template>
            <!-- <template v-slot:description>
                <p>
                    Mariah or Messiah was built as part of a hackathon with the aim of creating a fun (and rather silly!) Christmas card. Whilst generating publicity for Neverbland, it also helped raise money for the Hackney Winter Night Shelter charity. The quiz makes heavy use of the Greensock library to facilitate all the animations.
                    When you REALLY think about it, Christmas is about two people: Jesus Christ and Mariah Carey. One is the son of God, the other is an American singer with 8 Jack Russells and a 5 octave range. But which of these two seasonal superstars is responsible for the following quotes?
                    Let’s play Mariah or Messiah!
                </p>
            </template> -->
        </project-modal>
        <section class="py-7 py-lg-10" data-scroll-section>
            <div class="container">
                <div class="row justify-content-start mb-6 mb-lg-7">
                    <div class="col-md-8">
                        <p class="header" data-scroll data-scroll-speed="2.5">Selected projects</p>
                        <h1 class="title" data-scroll data-scroll-speed="1.5">
                            A few projects I had fun working on
                        </h1>
                    </div>
                </div>
                <div class="project__row">
                    <div class="project__column">
                        <TheProject v-for="project in projects.slice(0,3)" :key="project.id" :projectId="project.id" :projectLink="project.project_link" :mobile-num="project.mobile_num" :desktop-num="project.desktop_num" :width="project.width" :height="project.height" :containerWidth="project.container_width" :projectTitle="project.title" :projectTags="project.tags" :projectImage="project.project_image" @open="showProjectModal(project)"/>
                    </div>
                    <div class="project__column">
                        <TheProject v-for="project in projects.slice(3,6)" :key="project.id" :projectId="project.id" :projectLink="project.project_link" :mobile-num="project.mobile_num" :desktop-num="project.desktop_num" :width="project.width" :height="project.height" :containerWidth="project.container_width" :projectTitle="project.title" :projectTags="project.tags" :projectImage="project.project_image" @open="showProjectModal(project)"/>
                    </div>
                    <div class="project__column">
                        <TheProject v-for="project in projects.slice(6,9)" :key="project.id" :projectId="project.id" :projectLink="project.project_link" :mobile-num="project.mobile_num" :desktop-num="project.desktop_num" :width="project.width" :height="project.height" :containerWidth="project.container_width" :projectTitle="project.title" :projectTags="project.tags" :projectImage="project.project_image" @open="showProjectModal(project)"/>
                    </div>
                </div>
            </div>
        </section>
    </div>
</template>

<script>
import projects from '../projects'

export default {
    data() {
        return {
            projects,
            isProjectModalVisible: false,
            projectInfo: null,
        }
    },
    methods: {
        showProjectModal(item) {
            // TODO: To be continued later
            
            // this.projects.forEach(project => {
            //     if(project.id === item.id) {
            //         this.projectInfo = project
            //         console.log(this.projectInfo);
            //         this.isProjectModalVisible = true 

            //         // Add overlay
            //         let elem = document.createElement('div');
            //         elem.className = 'panel--overlay';
            //         document.body.appendChild(elem);
            //     }
            // }) 
        },
        closeProjectModal() {
            this.isProjectModalVisible = false

            // Remove overlay
            let backDrop = document.querySelector('.panel--overlay');
            backDrop.remove();
        }
    },
}
</script>