<template>
    <div>
        <h1>Event Listing</h1>
        <EventCard v-for="event in events" :key="event.id" :event="event"/>
    </div>
</template>

<script>
import EventCard from '@/components/EventCard.vue'
import EventService from '@/services/EventService';

export default {
    components: {
        EventCard,
    },
    data() {
        return {
            events: []
        }
    },
    created() {
            EventService.getEvents()
            .then(response => {
                this.events = response.data
                console.log(response.data)
            })
            .catch(error => {
                console.log('There was an error:' + error.response)
            })
    }
}
</script>