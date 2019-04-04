<template>
    <Page class="page">
        <ActionBar class="action-bar" title="Ajax List View">
            <NavigationButton text="Go Back"
                              android.systemIcon="ic_menu_back"
                              @tap="$navigateTo(App)"/>
        </ActionBar>


        <StackLayout orientation="vertical" width="100%" height="100%">

            <ActivityIndicator row="1" #activityIndicator busy="true"
                               v-if="loader"
                               (busyChange)="onBusyChanged($event)"
                               width="100" height="100"
                               class="activity-indicator">

            </ActivityIndicator>



            <Button class="btn btn-primary" @tap="onButtonTab" text="Fetch List" />

            <Label v-if="item_active" :text="item_active.name" />

            <ListView for="item in list" @itemTap="onItemTap">
                <v-template>
                    <Label :text="item.name"  />
                </v-template>
            </ListView>

        </StackLayout>


    </Page>
</template>

<script >
    import App from './App'
    const axios = require("axios");
    export default {
        props: [],
        data() {

            let obj = {
                App: App,
                loader: false,
                list: [],
                item_active: null
            };

            return obj;

        },
        methods:{
            //-----------------------------------
            startLoader: function()
            {
                this.loader = true;
            },
            //-----------------------------------
            stopLoader: function()
            {
                this.loader = false;
            },
            //-----------------------------------
            onButtonTab: function () {
                this.startLoader();
                axios.get('https://restcountries.eu/rest/v2/all')
                    .then(response => {
                        this.list = response.data
                        console.log("list", this.list);
                        this.stopLoader();
                    })
                    .catch(error => {
                        console.log(error);
                        this.stopLoader();
                    })
            },
            //-----------------------------------
            onItemTap: function (event)
            {
                this.item_active = event.item;

                console.log('item', event.item);
            },
            //-----------------------------------
            //-----------------------------------
            //-----------------------------------
        },

    }
</script>

<style scoped>

</style>
