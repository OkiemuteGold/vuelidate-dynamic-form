<template>
    <div>
        <FormPlanPicker
            v-if="currentStepNumber === 1"
            @updateData="processStep"
        />
        <FormUserDetails
            v-if="currentStepNumber === 2"
            @updateData="processStep"
        />
        <FormAddress v-if="currentStepNumber === 3" @updateData="processStep" />
        <FormReviewOrder
            v-if="currentStepNumber === 4"
            @updateData="processStep"
        />

        <div class="progress-bar">
            <div :style="`width: ${progress}%;`"></div>
        </div>

        <!-- Actions -->
        <div class="buttons">
            <button
                @click="goToPrevious"
                v-if="currentStepNumber > 1"
                class="btn-outlined"
            >
                Back
            </button>
            <button @click="goToNext" class="btn">Next</button>
        </div>

        <pre><code>{{form}}</code></pre>
    </div>
</template>

<script>
import FormPlanPicker from "./FormPlanPicker";
import FormUserDetails from "./FormUserDetails";
import FormAddress from "./FormAddress";
import FormReviewOrder from "./FormReviewOrder";

export default {
    name: "FormWizard",
    components: {
        FormPlanPicker,
        FormUserDetails,
        FormAddress,
        FormReviewOrder,
    },
    data() {
        return {
            currentStepNumber: 1,
            length: 4,
            form: {
                plan: null,
                email: null,
                name: null,
                password: null,
                address: null,
                recipient: null,
                chocolate: false,
                otherTreat: false,
            },
        };
    },
    computed: {
        progress() {
            return (this.currentStepNumber / this.length) * 100;
        },
    },
    methods: {
        goToPrevious() {
            this.currentStepNumber--;
        },
        goToNext() {
            this.currentStepNumber++;
        },
        processStep(stepData) {
            // Object.assign copies the properties of an object to another one
            Object.assign(this.form, stepData);
        },
    },
};
</script>

<style lang="scss" scoped>
</style>