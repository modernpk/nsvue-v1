<template>
    <Page>
        <ActionBar title="Welcome to NativeScript-Vue!"/>


        <StackLayout>
            <Button text="List View" @tap="$navigateTo(ListPage)" />
        </StackLayout>

    </Page>
</template>

<script >
  import ListPage from './ListPage'
  export default {
    data() {
      return {
          msg: 'Hello World!',
          ListPage: ListPage
      }
    }
  }
</script>

<style scoped>
    ActionBar {
        background-color: #53ba82;
        color: #ffffff;
    }

    .message {
        vertical-align: center;
        text-align: center;
        font-size: 20;
        color: #333333;
    }
</style>
