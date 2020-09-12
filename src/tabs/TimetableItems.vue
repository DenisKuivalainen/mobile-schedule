<template>
<view>
    <ListItem itemDivider>
        <Text>{{day.time}}</Text>
    </ListItem>                    
    <ListItem v-for="(val, k) in day" :key="k">
        <view>
            <Text class="subject-title">{{val.subjects.name}}</Text>
            <Text>&#9702; {{val.subjects.desc}}</Text>
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
        day: {type: Array}
    },
}
</script>

<style>
.subject-title {
    font-weight: bold;
    margin-bottom: 5;
}
</style>