<template>
  <Container>
    
    <status-bar
      background-color="#3F51B5"
      bar-style="light-content"
    />
    <ScrollView :enabled="true">
      <RefreshControl :enabled="true" :refreshing="refreshing" :onRefresh="onRefresh" >
        <view class="full-screen" :style="{height: screenHeight}">
          <Tabs>
            <Tab heading="Расписание на день">
              <H1 class="day-title">Пн, 14.09</H1>
              <ScrollView>
                <List>
                  <ListItem itemDivider>
                    <Text>0:10-11:40</Text>
                  </ListItem>                    
                  <ListItem>
                    <view>
                      <Text class="subject-title">История отечественной литературы: древнерусская литература - литература XIX века, 1 часть</Text>
                      <Text>&#9702; доц. Е.Г.Николаева (л.), а. 109, с 15.09</Text>
                    </view>
                  </ListItem>
                  <ListItem>
                    <view>
                      <Text class="subject-title">История отечественной литературы: древнерусская литература - литература XIX века, 1 часть</Text>
                      <Text>&#9702; доц. Е.Г.Николаева (л.), а. 109, с 15.09</Text>
                    </view>
                  </ListItem>
                  <ListItem itemDivider>
                    <Text>0:10-11:40</Text>
                  </ListItem>                    
                  <ListItem>
                    <view>
                      <Text class="subject-title">История отечественной литературы: древнерусская литература - литература XIX века, 1 часть</Text>
                      <Text>&#9702; доц. Е.Г.Николаева (л.), а. 109, с 15.09</Text>
                    </view>
                  </ListItem>
                  <ListItem>
                    <view>
                      <Text class="subject-title">История отечественной литературы: древнерусская литература - литература XIX века, 1 часть</Text>
                      <Text>&#9702; доц. Е.Г.Николаева (л.), а. 109, с 15.09</Text>
                    </view>
                  </ListItem>
                </List>
              </ScrollView>
            </Tab>
            <Tab heading="Календарь">
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
            </Tab>
            <Tab heading="Loading">
              <view class="loading">
                <H3 class="loading-text">Расписание загружается</H3>
                <Spinner color="#3F51B5" />
              </view>
            </Tab>
            <Tab heading="Error">
              <H3 class="error">На сервере возникла ошибка. Если при повторной загрузке она не пропадет, свяжитесь с администратором.</H3>
            </Tab>
          </Tabs>    
        </view>
      </RefreshControl>
    </ScrollView>
  </Container>
</template>

<script>
import { Container, Header, Content, Tab, Tabs, List, ListItem, H1, H3, Spinner, Grid, Col } from 'native-base';
import { ScrollView, RefreshControl, Dimensions } from 'react-native';

export default {
  name: 'App',

  components: { 
    Container: Container, 
    Header: Header,
    Content: Content,
    Tab: Tab,
    Tabs: Tabs,
    ScrollView: ScrollView,
    RefreshControl: RefreshControl,
    Dimensions: Dimensions,
    List: List,
    ListItem: ListItem,
    H1: H1,
    H3: H3,
    Spinner: Spinner,
    Grid: Grid,
    Col: Col,
    },

  data: function() {
    return {
      refreshing: false,
      screenHeight: Dimensions.get('window').height,
      type: "danger"
    }
  },

methods: {
  onRefresh(){
    this.refreshing = true
    console.log("hello")
    this.refreshing = false
  },
}
}
</script>

<style>
.container {
  background-color: white;
  align-items: center;
  justify-content: center;
  flex: 1;
}
.text-color-primary {
  color: blue;
}
.footer {
  position: absolute;
  bottom: 0;
}
.subject-title {
  font-weight: bold;
  margin-bottom: 5;
}
.day-title {
  margin-bottom: 5;
  margin-top: 10;
  margin-left: auto;
  margin-right: auto;
}
.error {
  position: absolute;          
  top: 30%;                         
  transform: translate(0, -50%);
  text-align: center;
  margin: 20;
  color: red;
  font-weight: bold;
}
.loading {
  top: 30%;                         
  transform: translate(0, -50%);
}
.loading-text {
  text-align: center;
  margin: 20;
}
.heading {
  text-align: center;
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
}
.button-active {
  background-color: brown;
}
</style>
