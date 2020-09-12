<template>
    <ScrollView>
        <List>
            <TimetableItems v-for="(val, k) in day" :key="k" v-bind:day="val" />
        </List>
    </ScrollView>
</template>

<script>
import { List } from 'native-base';
import { ScrollView } from 'react-native';
import TimetableItems from './TimetableItems';

export default {
    name: 'Timetable',

    components: {
        ScrollView,
        List,
        TimetableItems
    },

    props: {
        day: {type: Array}
    },
}
</script>

<style>

</style>