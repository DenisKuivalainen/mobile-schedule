<template>
  <H3 class="error">На сервере возникла ошибка. Если при повторной загрузке она не пропадет, свяжитесь с администратором.</H3>
</template>

<script>
import { H3 } from 'native-base';

export default {
  name: 'Error',

  components: {
    H3: H3,
  }
}
</script>

<style>
.error {
  position: absolute;          
  top: 20;
  text-align: center;
  margin: 20;
  color: #b600bf;
  font-weight: bold;
}
</style>