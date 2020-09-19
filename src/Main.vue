<template>
    <ScrollView :enabled="true">
        <view :style="{height: screenHeight, backgroundColor: 'black'}">
            <Tabs
                :tabBarUnderlineStyle="{backgroundColor: 'white'}"
            >
                <Tab 
                    :tabStyle="{backgroundColor: '#b600bf'}" 
                    :activeTabStyle="{backgroundColor: '#b600bf'}"
                    :textStyle="{color: '#fbbaff'}"
                    :activeTextStyle="{color: 'white', fontWeight: 'bold'}"
                    class="tab-bg" 
                    heading="Расписание на день"
                >
                    <Timetable 
                        v-bind:day="getTimetable()"
                        v-bind:dayTitle="getDayTitle()"
                        v-bind:refreshing="refreshing" 
                        @onRefresh="onRefresh" 
                    />
                </Tab>
                <Tab 
                    :tabStyle="{backgroundColor: '#b600bf'}" 
                    :activeTabStyle="{backgroundColor: '#b600bf'}"
                    :textStyle="{color: '#fbbaff'}"
                    :activeTextStyle="{color: 'white', fontWeight: 'bold'}"
                    class="tab-bg" 
                    heading="Календарь"
                >
                    <Week 
                        v-bind:day="day"
                        v-bind:week="week"
                        v-bind:todayDay="getCurrentDay()"
                        v-bind:todayWeek="data.week"
                        @setTimetableDay="setTimetableDay"
                    />
                </Tab>
            </Tabs>    
        </view>
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
            day: this.getCurrentDay(),
            week: this.data.week,
            dayNames: ["monday", "monday", "tuesday", "wednesday", "thursday", "friday", "saturday"],
            dayNamesShort: ["ПН", "ПН", "ВТ", "СР", "ЧТ", "ПТ", "СБ"]
        }
    },

    methods: {
        onRefresh() {
            this.refreshing = true;
            this.$emit("getJsonData");
            this.day = this.getCurrentDay();
            this.week = this.data.week;
            this.refreshing = false;
        },

        setTimetableDay(arr) {
            this.day = arr[0];
            this.week = arr[1];
        },

        getCurrentDay() {
            var today = new Date();
            return today.getDay();
        },

        getDayTitle() {
            let a = this.dayNamesShort[this.day];
            let b = this.week ? "числитель" : "знаменатель";
            return a + ', ' + b;
        },
 
        getTimetable() {
            let arr = [];
            let ttl = this.data.days[this.dayNames[this.day]];

            for (let i = 0; i < ttl.length; i++) {
                let time = ttl[i].time;
                let subjects = [];

                if(ttl[i].subjects.length === 1) {
                    subjects.push(ttl[i].subjects[0]);
                } else {

                    let code;
                    let subjectsSubarray = ttl[i].subjects;

                    if(this.week) {
                        code = subjectsSubarray[0].code;
                    } else {
                        code = subjectsSubarray[subjectsSubarray.length - 1].code;
                    }

                    for (let j = 0; j < subjectsSubarray.length; j++) {
                        (subjectsSubarray[j].code === code) && subjects.push(subjectsSubarray[j]);                       
                    }
                }
                
                if(subjects[0].name !== "") {
                    arr.push({time: time, subjects: subjects});
                }
            }
            return arr;
        }
    }
}
</script>

<style>
.tab-bg {
    background-color: black;
}
</style>