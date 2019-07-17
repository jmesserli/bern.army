<template>
  <div>
    <b-progress :max="43" height="2rem">
      <b-progress-bar :value="18" variant="success">
        RS: 18 / 18
      </b-progress-bar>
      <b-progress-bar :value="9" :animated="true">
        DD: 9 / 25
      </b-progress-bar>
    </b-progress>
  </div>
</template>

<script>
export default {
  name: 'RsWoche'
}
</script>
