<script setup>
import { ref } from 'vue';
import MetricsAcrossThresholds from './MetricsAcrossThresholds.vue';
import ROC from './ROC.vue';

const currState = ref('graphs');

const githubUrl = "https://github.com/peek00";
const linkedinUrl = "https://www.linkedin.com/in/lim-xun-yi/";
const iconWidth = ref(49);
const iconHeight = ref(48);

const  expandGithubIcon = () => {
  iconWidth.value = 49 + 6; 
  iconHeight.value = 48 + 6;
};

const resetGithubIcon = () => {
  iconWidth.value = 49;
  iconHeight.value = 48;
};

const  expandLinkedInIcon = () => {
  iconWidth.value = 49 + 6; 
  iconHeight.value = 48 + 6;
};

const resetLinkedInIcon = () => {
  iconWidth.value = 49;
  iconHeight.value = 48;
};

const toggleState = (state) => {
  currState.value = state;
};



</script>

<style>
.custom-button{
background: none;
border: none;
padding: 0;
margin: 0;
cursor: pointer;
font-size: 1.5rem;
color: rgb(68, 68, 68);
}

.active-button{
    text-decoration: underline;
    color: black;
    font-weight: bold;
}
a svg , a img {
  transition: all 0.3s ease; /* Add a transition effect to animate the size change */
}
</style>

<template>
        <div class="row pt-3 justify-content-center bg-white">
            <button class="col-xl-1 custom-button" :class="{ 'active-button': currState === 'graphs' }" @click="toggleState('graphs')">Graphs</button>
            <button class="col-xl-1 custom-button" :class="{ 'active-button': currState === 'learn' }" @click="toggleState('learn')">Takeaways</button>
        </div>
        <div class="row bg-white" >
            <div>
                <div v-if="currState == 'graphs'" class="row pt-5 d-flex justify-content-center text-center">
                    <MetricsAcrossThresholds></MetricsAcrossThresholds>
                </div>
                <div v-if="currState == 'graphs'" class="row pt-5 d-flex justify-content-center text-center">
                    <ROC></ROC>
                </div>
                <div v-if="currState=='learn'" class="row pt-5 d-flex px-5"> 
                    <div class="col-xl-8 offset-xl-2 ">               
                        This project was built during the course of Heicoder-AI300. Through the course, some takeaways I had where:
                        <ul class="px-5">
                            <li>
                                Converting machine learning notebook into a Object-Oriented Programming (OOP) style with Python scripts.
                            </li>
                            <li>
                                Building  reusable abstract base classes with Python that made swapping out models, preprocessing steps, data sources easier.
                            </li>
                            <li>
                                Pickling models and preprocessing objects to be used in production.
                            </li>
                            <li>
                                Dockerizing and deploying an image to AWS EC2.
                            </li>
                            <li>
                                Learnt how to implement a CI/CD workflow.
                            </li>
                        </ul>
                        Beyond the course goals, I decided to use this as an opportunity to learn how to deploy a Vue frontend application.
                        I used Vercel to deploy my Vue application and AWS EC2 to deploy my backend image. I ran into some issues with SSL Certificates 
                        and had to learn how to configure my backend to use HTTPS. This involved:
                        
                        <ul class="px-5">
                            <li>
                                Obtaining a domain name using FreeDNS
                            </li>
                            <li>
                                Generating a SSL Certificate using Certbot on the Amazon EC2 instance.
                            </li>
                        </ul>
                    Overall, from this course I learnt a lot about productionizing machine learning models and deploying them. 
                    A key takeaway was definitely how to write good code that could be swapped out quickly later on.
                    </div>
                </div>
                <div class="row p-5 mx-5 text-end justify-content-end">
                    <div class="mx-5" style="width: 65px">
                        <a :href="githubUrl" @mouseenter="expandGithubIcon" @mouseleave="resetGithubIcon">
                            <svg :width="iconWidth" :height="iconHeight" viewBox="0 0 98 96" xmlns="http://www.w3.org/2000/svg">
                                <path fill-rule="evenodd" clip-rule="evenodd" d="M48.854 0C21.839 0 0 22 0 49.217c0 21.756 13.993 40.172 33.405 46.69 2.427.49 3.316-1.059 3.316-2.362 0-1.141-.08-5.052-.08-9.127-13.59 2.934-16.42-5.867-16.42-5.867-2.184-5.704-5.42-7.17-5.42-7.17-4.448-3.015.324-3.015.324-3.015 4.934.326 7.523 5.052 7.523 5.052 4.367 7.496 11.404 5.378 14.235 4.074.404-3.178 1.699-5.378 3.074-6.6-10.839-1.141-22.243-5.378-22.243-24.283 0-5.378 1.94-9.778 5.014-13.2-.485-1.222-2.184-6.275.486-13.038 0 0 4.125-1.304 13.426 5.052a46.97 46.97 0 0 1 12.214-1.63c4.125 0 8.33.571 12.213 1.63 9.302-6.356 13.427-5.052 13.427-5.052 2.67 6.763.97 11.816.485 13.038 3.155 3.422 5.015 7.822 5.015 13.2 0 18.905-11.404 23.06-22.324 24.283 1.78 1.548 3.316 4.481 3.316 9.126 0 6.6-.08 11.897-.08 13.526 0 1.304.89 2.853 3.316 2.364 19.412-6.52 33.405-24.935 33.405-46.691C97.707 22 75.788 0 48.854 0z" fill="#24292f"/>
                            </svg>
                        </a>
                    </div>
                    <div class="" style="width: 65px">
                        <a :href="linkedinUrl" @mouseenter="expandLinkedInIcon" @mouseleave="resetLinkedInIcon">
                            <img :width="iconWidth" :height="iconHeight" src="../assets/LI-In-Bug.png" alt="vue">
                        </a>
                    </div>
                </div>
            
            </div>
        </div>
        
</template>