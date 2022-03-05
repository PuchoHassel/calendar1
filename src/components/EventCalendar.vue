<script setup>
import '@fullcalendar/core/vdom'
import { ref, reactive } from 'vue'
import FullCalendar from '@fullcalendar/vue3/dist/main'
import dayGridPlugin from '@fullcalendar/daygrid'
import timeGridPlugin from '@fullcalendar/timegrid'
import listPlugin from '@fullcalendar/list'
import interactionPlugin from '@fullcalendar/interaction'


const id = ref(0)
FullCalendar
const options = reactive({
    plugins: [dayGridPlugin, timeGridPlugin, listPlugin, interactionPlugin],
     initialView: 'timeGridDay',
     headerToolbar: {
         left: 'prev,next today',
         center: 'title',
         right: 'timeGridWeek,listMonth,timeGrid'
     },
     editable: true,
     selectable: true,
     weekends: true,
     select: (arg) => {
         id.value = prompt('Name:') 
         if(id.value == null || id.value == '') {
            return
         }
        
        const cal = arg.view.calendar
        cal.unselect()
        cal.addEvent({
             id: `${id.value}`,
             title: `${id.value}`,
             start: arg.start,
             end: arg.end,
        })
    },

    eventClick: (arg) => {
        if( confirm('Are you sure you want to delete your appointment?') == true) {
            arg.event.remove()            
        }
     },
    //  businessHours: {
    // // days of week. an array of zero-based day of week integers (0=Sunday)
    // daysOfWeek: [ 0, 1, 2, 3, 4, 5, 6 ], // Monday - Thursday

    // startTime: '08:00', // a start time (10am in this example)
    // endTime: '22:00', // an end time (6pm in this example)
    // }
 })


</script>

<template>
    <FullCalendar v-bind:options="options" />
</template>

<style>

</style>