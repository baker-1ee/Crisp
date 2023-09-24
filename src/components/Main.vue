<template>
  <div class="main">
    <div class="auth-wrapper">
      <div class="auth-inner">
        <router-view/>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Main'
}
</script>

<style scoped>

.main {
  position: absolute;
  left: 240px; /* 메뉴 접힐 때 동적으로 변해야함 */
  top: 56px;
  width: calc(100% - 240px);
  height: calc(100% - 56px);
  background-color: #d1e3f8;
}

.auth-wrapper {
  display: flex;
  justify-content: center; /* 가로 가운데 정렬 */
  align-items: center; /* 세로 가운데 정렬 */
  height: 100%; /* 부모 높이에 맞추기 */
  /*flex-direction: column;*/
  text-align: left;
}

.auth-inner {
  width: 450px;
  margin: auto;
  background: #ffffff;
  box-shadow: 0 14px 80px rgba(34, 35, 58, 0.2);
  padding: 40px 55px 45px 55px;
  border-radius: 15px;
  transition: all .3s;
}
</style>
