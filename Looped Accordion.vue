
<script setup>
import { ref } from 'vue';

const activeExamIndex = ref(null);

const toggleExams = (index) => {
    if (activeExamIndex.value === index) {
        activeExamIndex.value = null;
    } else {
        activeExamIndex.value = index;
    }
};

const exams = ref([
    {
        title: 'Exam Title 1',
        items: [
            { title: 'Exam Item 1', duration: '60 mins' },
            { title: 'Exam Item 2', duration: '90 mins' }
            // Add more items if needed
        ]
    },
    {
        title: 'Exam Title 2',
        items: [
            { title: 'Exam Item 1', duration: '60 mins' },
            { title: 'Exam Item 2', duration: '90 mins' }
            // Add more items if needed
        ]
    },
    // Add more exams if needed
]);

</script>

<template>
    <div class="mt-2.5">
        <div class="accordion">
            <div v-for="(exam, index) in exams" :key="index" class="border border-ash-850 rounded-3 mb-2" :class="{ 'border-primary': activeExamIndex === index }">
                <div class="py-2.5 px-5 bg-white flex items-center justify-between cursor-pointer rounded-3" @click="toggleExams(index)">
                    <div class="">
                        <span class="text-black-500 font-normal text-base">{{ exam.title }}</span>
                    </div>
                    <svg :class="{ rotated: activeExamIndex === index }" xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" viewBox="0 0 16 16" class="accordion-icon">
                        <path fill-rule="evenodd" d="M1.646 4.646a.5.5 0 0 1 .708 0L8 10.293l5.646-5.647a.5.5 0 0 1 .708.708l-6 6a.5.5 0 0 1-.708 0l-6-6a.5.5 0 0 1 0-.708z" />
                    </svg>
                </div>
                <div v-if="activeExamIndex === index" class="bg-white rounded-3 py-2.5 px-5">
                    <div v-for="(item, itemIndex) in exam.items" :key="itemIndex" class="flex justify-between items-center mt-2.5">
                        <div class="flex gap-2 items-center">
                            <div>
                                <svg width="16" height="16" viewBox="0 0 16 16" fill="none" xmlns="http://www.w3.org/2000/svg">
                                    <path d="M14 0.5H5C4.175 0.5 3.5 1.175 3.5 2V11C3.5 11.825 4.175 12.5 5 12.5H14C14.825 12.5 15.5 11.825 15.5 11V2C15.5 1.175 14.825 0.5 14 0.5ZM14 11H5V2H14V11ZM2 3.5H0.5V14C0.5 14.825 1.175 15.5 2 15.5H12.5V14H2V3.5ZM11 8V5.75C11 5.3375 10.6625 5 10.25 5H8.75V8.75H10.25C10.6625 8.75 11 8.4125 11 8ZM9.5 5.75H10.25V8H9.5V5.75ZM12.5 7.25H13.25V6.5H12.5V5.75H13.25V5H11.75V8.75H12.5V7.25ZM6.5 7.25H7.25C7.6625 7.25 8 6.9125 8 6.5V5.75C8 5.3375 7.6625 5 7.25 5H5.75V8.75H6.5V7.25ZM6.5 5.75H7.25V6.5H6.5V5.75Z" fill="#5D5D5D" />
                                </svg>
                            </div>
                            <div class="text-ash-1200 font-normal text-sm">
                                {{ item.title }}
                            </div>
                        </div>
                        <div class="text-ash-1200 text-primary shade-class rounded-full p-1.5">
                            {{ item.duration }}
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<style scoped>
.accordion-item {
    border-bottom: 1px solid #ddd;
}

.accordion-header {
    padding: 10px;
    cursor: pointer;
    background: #f5f5f5;
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.accordion-content {
    padding: 10px;
    background: #fff;
}

.accordion-icon {
    transition: transform 0.3s;
}

.rotated {
    transform: rotate(180deg);
}
</style>