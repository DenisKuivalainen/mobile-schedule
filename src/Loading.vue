<template>
    <view class="loading">
        <H3 class="loading-text">Расписание загружается...</H3>
        <Spinner color="#3F51B5" />
    </view>
</template>

<script>
import { H3, Spinner } from 'native-base';

export default {
    name: 'Loading',

    components: {
        H3: H3,
        Spinner: Spinner,
    }
}
</script>

<style>
.loading {
    top: 20;
}
.loading-text {
    text-align: center;
    margin: 20;
}
</style>