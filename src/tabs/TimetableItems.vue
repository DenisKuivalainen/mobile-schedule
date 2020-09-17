<template>
<view>
    <ListItem itemDivider>
        <Text>{{day.time}}</Text>
    </ListItem>                    
    <ListItem v-for="(val, k) in day.subjects" :key="k">
        <view>
            <Text class="subject-title">{{val.name}}</Text>
            <Text v-if="val.desc !== ''">&#9702; {{val.desc}}</Text>
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
}
</style>