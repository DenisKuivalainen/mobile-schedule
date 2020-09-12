<template>
    <Grid class="loading">
        <Col>
            <H3 class="heading">Числитель</H3>
            <Text class="heading">Текущая неделя</Text>
            <touchable-opacity class="button" :style="{backgroundColor: '#3F51B5'}">
                <Text>Понедельник</Text>
            </touchable-opacity>
            <touchable-opacity class="button" :style="{backgroundColor: '#bfbfbf'}">
                <Text>Вторник</Text>
            </touchable-opacity>
            <touchable-opacity class="button" :style="{backgroundColor: '#bfbfbf'}">
                <Text>Среда</Text>
            </touchable-opacity>
            <touchable-opacity class="button" :style="{backgroundColor: '#bfbfbf'}">
                <Text>Четверг</Text>
            </touchable-opacity>
            <touchable-opacity class="button" :style="{backgroundColor: '#bfbfbf'}">
                <Text>Пятница</Text>
            </touchable-opacity>
            <touchable-opacity class="button" :style="{backgroundColor: '#bfbfbf'}">
                <Text>Суббота</Text>
            </touchable-opacity>
        </Col>
        <Col>
            <H3 class="heading">Знаменатель</H3>
            <Text class="heading"></Text>
            <touchable-opacity class="button" :style="{backgroundColor: '#bfbfbf'}">
                <Text>Понедельник</Text>
            </touchable-opacity>
            <touchable-opacity class="button" :style="{backgroundColor: '#bfbfbf'}">
                <Text>Вторник</Text>
            </touchable-opacity>
            <touchable-opacity class="button" :style="{backgroundColor: '#bfbfbf'}">
                <Text>Среда</Text>
            </touchable-opacity>
            <touchable-opacity class="button" :style="{backgroundColor: '#bfbfbf'}">
                <Text>Четверг</Text>
            </touchable-opacity>
            <touchable-opacity class="button" :style="{backgroundColor: '#bfbfbf'}">
                <Text>Пятница</Text>
            </touchable-opacity>
            <touchable-opacity class="button" :style="{backgroundColor: '#bfbfbf'}">
                <Text>Суббота</Text>
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