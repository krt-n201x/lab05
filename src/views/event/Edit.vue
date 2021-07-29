<template>
  <p>Edit the event here</p>
  <button @click="edit">edit Me</button>
</template>

<script>
export default {
  props: ['event'],
  inject: ['GStore'], //<---- Inject the Global Store
  methods: {
    edit() {
      this.GStore.flashMessage =
        'You are seccessfully edited for ' + this.event.title
      setTimeout(() => {
        //After 3 seconds remove it
        this.GStore.flashMessage = ''
      }, 3000)
      //Set a flash message to appear on the next page loaded which says
      this.$router.push({
        name: 'EventDetails',
        params: { id: this.event.id }
      })
    }
  }
}
</script>
