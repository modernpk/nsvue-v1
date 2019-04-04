<template>
    <Page>
        <ActionBar title="Welcome to NativeScript-Vue!"/>
        <GridLayout columns="*" rows="*">


            <Label class="message" :text="msg" col="0" row="0"/>
        </GridLayout>

        <StackLayout>
            <Button text="To Details directly" @tap="$navigateTo(detailPage)" />
        </StackLayout>

    </Page>
</template>

<script >
    import DetailPage from './DetailPage'
  export default {
    data() {
      return {
          msg: 'Hello World!',
          detailPage: DetailPage
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
