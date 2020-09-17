<template>
    <Grid class="loading">
        <Col>
            <H3 class="heading">Числитель</H3>
            <Text class="heading">{{getWeekId(true)}}</Text>
            <touchable-opacity class="button" :style="{backgroundColor: getBackground(1, true)}" v-on:press="setTimetableDay(1, true)">
                <Text :style="{color: getColor(1, true)}">Понедельник</Text>
            </touchable-opacity>
            <touchable-opacity class="button" :style="{backgroundColor: getBackground(2, true)}" v-on:press="setTimetableDay(2, true)">
                <Text :style="{color: getColor(2, true)}">Вторник</Text>
            </touchable-opacity>
            <touchable-opacity class="button" :style="{backgroundColor: getBackground(3, true)}" v-on:press="setTimetableDay(3, true)">
                <Text :style="{color: getColor(3, true)}">Среда</Text>
            </touchable-opacity>
            <touchable-opacity class="button" :style="{backgroundColor: getBackground(4, true)}" v-on:press="setTimetableDay(4, true)">
                <Text :style="{color: getColor(4, true)}">Четверг</Text>
            </touchable-opacity>
            <touchable-opacity class="button" :style="{backgroundColor: getBackground(5, true)}" v-on:press="setTimetableDay(5, true)">
                <Text :style="{color: getColor(5, true)}">Пятница</Text>
            </touchable-opacity>
            <touchable-opacity class="button" :style="{backgroundColor: getBackground(6, true)}" v-on:press="setTimetableDay(6, true)">
                <Text :style="{color: getColor(6, true)}">Суббота</Text>
            </touchable-opacity>
        </Col>
        <Col>
            <H3 class="heading">Знаменатель</H3>
            <Text class="heading">{{getWeekId(false)}}</Text>
            <touchable-opacity class="button" :style="{backgroundColor: getBackground(1, false)}" v-on:press="setTimetableDay(1, false)">
                <Text :style="{color: getColor(1, false)}">Понедельник</Text>
            </touchable-opacity>
            <touchable-opacity class="button" :style="{backgroundColor: getBackground(2, false)}" v-on:press="setTimetableDay(2, false)">
                <Text :style="{color: getColor(2, false)}">Вторник</Text>
            </touchable-opacity>
            <touchable-opacity class="button" :style="{backgroundColor: getBackground(3, false)}" v-on:press="setTimetableDay(3, false)">
                <Text :style="{color: getColor(3, false)}">Среда</Text>
            </touchable-opacity>
            <touchable-opacity class="button" :style="{backgroundColor: getBackground(4, false)}" v-on:press="setTimetableDay(4, false)">
                <Text :style="{color: getColor(4, false)}">Четверг</Text>
            </touchable-opacity>
            <touchable-opacity class="button" :style="{backgroundColor: getBackground(5, false)}" v-on:press="setTimetableDay(5, false)">
                <Text :style="{color: getColor(5, false)}">Пятница</Text>
            </touchable-opacity>
            <touchable-opacity class="button" :style="{backgroundColor: getBackground(6, false)}" v-on:press="setTimetableDay(6, false)">
                <Text :style="{color: getColor(6, false)}">Суббота</Text>
            </touchable-opacity>
        </Col>
    </Grid>
</template>

<script>
import { Grid, Col, H3 } from 'native-base';

export default {
    name: 'Week',

    components: {
        Grid: Grid,
        Col: Col,
        H3: H3,
    },
    
    props: {
        day: {type: Number},
        week: {type: Boolean},
        todayDay: {type: Number},
        todayWeek: {type: Boolean}
    },

    methods: {
        setTimetableDay(day, week) {
            this.$emit("setTimetableDay", [day, week]);
        },

        getWeekId(id) {
            return id === this.todayWeek ? "Текущая неделя" : " ";
        },

        getBackground(day, week) {
            let a = this.todayDay === 0 ? 1 : this.todayDay;
            return (a === day && week === this.todayWeek) ? '#3F51B5' : '#bfbfbf';
        },

        getColor(day, week) {
            let a = this.todayDay === 0 ? 1 : this.todayDay;
            return (a === day && week === this.todayWeek) ? 'white' : 'black';
        }
    }
}
</script>

<style>
.loading {
    top: 30%;                         
    transform: translate(0, -50%);
}
.button {
    margin-top: 10;
    margin-left: 20;
    margin-right: 20;
    padding: 5;
    height: 40;
    border-radius: 3;
    align-items: center;
    justify-content: center;
},
.heading {
    text-align: center;
}
</style>