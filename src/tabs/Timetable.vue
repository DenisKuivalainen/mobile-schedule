<template>
    <ScrollView>
        <RefreshControl :enabled="true" :refreshing="refreshing" :onRefresh="getRefresh" :colors="['#3F51B5']" >
            <H3 class="day-name">
                {{dayTitle}}
            </H3>
            <List>
                <TimetableItems v-for="(val, k) in day" :key="k" v-bind:day="val" />
            </List>
        </RefreshControl>
    </ScrollView>
</template>

<script>
import { List, H3 } from 'native-base';
import { ScrollView } from 'react-native';
import TimetableItems from './TimetableItems';

export default {
    name: 'Timetable',

    components: {
        ScrollView,
        List,
        TimetableItems,
        H3
    },

    props: {
        day: {type: Array},
        refreshing: {type: Boolean},
        dayTitle: {type: String}
    },

    methods: {
        getRefresh() {
            this.$emit("onRefresh");
        }
    }
}
</script>

<style>
.day-name {
    padding-top: 10;
    margin-bottom: 10;
    text-align: center;
    font-weight: bold;
    color: white;
}
</style>