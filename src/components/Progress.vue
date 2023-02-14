<template>
  <div class="progress">
    <div class="progress-bar bg-warning" role="progressbar" :style="{ width: progress + '%' }" aria-valuenow="50" aria-valuemin="0" aria-valuemax="100">
      {{ currentItem }}/10
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      currentItem: 0,
      progress: 0
    }
  },
  created() {
    this.emitter.on('progressBarUpdated', (productCount) => {
      this.currentItem = productCount
      this.progress = productCount * 10
    })
    this.emitter.on('productDeleted', (productCount) => {
      this.currentItem = productCount
      this.progress = productCount * 10
    })
  }
}
</script>