<template>
    <ScrollView :enabled="true">
        <RefreshControl :enabled="true" :refreshing="refreshing" :onRefresh="onRefresh" :colors="['#3F51B5']">
            <view :style="{height: screenHeight}">
                <Tabs>
                    <Tab heading="Расписание на день">
                        <Timetable v-bind:day="getTimetable()"/>
                    </Tab>
                    <Tab heading="Календарь">
                        <Week />
                    </Tab>
                </Tabs>    
            </view>
        </RefreshControl>
    </ScrollView>
</template>

<script>
import { Tab, Tabs } from 'native-base';
import { ScrollView, RefreshControl, Dimensions } from 'react-native';

import Timetable from './tabs/Timetable';
import Week from './tabs/Week';

export default {
    name: 'Main',

    components: {
        Tab,
        Tabs,
        ScrollView,
        RefreshControl,
        Dimensions,
        Timetable,
        Week
    },

    props: {
        loadingJson: {type: Boolean},
        data: {type: Object}
    },

    data: function() {
        return {
            screenHeight: Dimensions.get('window').height,
            refreshing: false,
            week: true,
            days: {},
            day: {},
            dayType: 0,
            dayNames: ["monday", "monday", "tuesday", "wednesday", "thursday", "friday", "saturday"]
        }
    },

    watch: {
        data: function(oldData, newData) {
            this.setInfo();
        }
    },

    methods: {
        onRefresh() {
            this.refreshing = true;
            this.$emit("getJsonData");
            this.refreshing = false;
        },
        setInfo() {
            this.week = this.data.week;
            this.days = this.data.days;
            this.setCurrentDay();
        },
        setDay(day, opt) {
            this.day = this.days[this.dayNames[day]];
            this.dayType = opt;
        },
        setCurrentDay() {
            var today = new Date();
            this.setDay(today.getDay(), this.week ? 0 : 1);
        },
        getTimetable() {
            let arr = [];
            let ttl = this.day;

            for (let i = 0; i < ttl.length; i++) {
                let time = ttl[i].time;
                let subjects = [];

                if(ttl[i].subjects.length = 1) {
                    subjects.push(ttl[i].subjects[0]);
                } else {

                    let code;
                    let subjectsSubarray = ttl[i].subjects;

                    if(dayType === 0) {
                        code = subjectsSubarray[0].code;
                    } else {
                        code = subjectsSubarray[subjectsSubarray.length].code;
                    }

                    for (let j = 0; j < subjectsSubarray.length; j++) {
                        if(subjectsSubarray[j].code === code) {
                            subjects.push(subjectsSubarray[j]);
                        }
                        
                    }
                }
                
                arr.push({time: time, subjects: subjects});
            }
            return arr;
        }
    }
}
</script>

<style>

</style>