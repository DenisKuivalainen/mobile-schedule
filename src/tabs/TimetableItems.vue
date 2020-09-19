<template>
<view>
    <ListItem class="time-row" itemDivider>
        <Text class="time">{{day.time}}</Text>
    </ListItem>                    
    <ListItem class="content-row" v-for="(val, k) in day.subjects" :key="k">
        <view>
            <Text class="subject-title">{{val.name}}</Text>
            <Text class="subject-desc" v-if="val.desc !== ''">&#9702; {{val.desc}}</Text>
        </view>
    </ListItem>
</view>
</template>

<script>
import { ListItem } from 'native-base';

export default {
    name: 'TimetableItems',

    components: {
        ListItem: ListItem,
    },

    props: {
        day: {type: Object}
    },
}
</script>

<style>
.subject-title {
    font-weight: bold;
    margin-bottom: 5;
    color: white;
}
.subject-desc {
    color: white;
}
.time {
    font-weight: bold;
    color: white;
}
.time-row {
    background-color: #b600bf;
    /* border-color: #b600bf;
    border-bottom-width: 1; */
    margin-top: 5;

}
.content-row {
    border-width: 0;
}
</style>