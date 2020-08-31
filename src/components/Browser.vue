<template>
  <div>
    <iframe :src="url"></iframe>
  </div>
</template>

<script>
export default {
    name: 'Browser',
    props: ['url'],
}
</script>

<style scoped>
  div {
    display: flex;
    justify-content: center;
    width: 100%;
  }
  iframe {
    width: 99%;
    height: 100%;
    
  }

  @media (max-height: 400px) {
    div {
      height: 76vh;
    }
  }
  @media (min-height: 401px) {
    div {
      height: 79vh
    }
  }
  @media (min-height: 600px) {
    div {
      height: 87vh
    }
  }
</style>