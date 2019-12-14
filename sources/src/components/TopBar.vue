<template>
<v-toolbar color="blue darken-3" dark app :clipped-left="$vuetify.breakpoint.mdAndUp" fixed>
    <v-toolbar-title style="width: 300px" class="text-xs-left">
        <v-toolbar-side-icon @click.stop="value.drawer = !value.drawer"></v-toolbar-side-icon>
        <span class="hidden-sm-and-down">BIZFLY-ADS</span>
    </v-toolbar-title>
    <v-spacer></v-spacer>
    <v-btn icon large @click="$router.push({path: '/profile'})">
        <v-avatar size="34px">
            <img :src="basicImg" alt="Vuetify">
        </v-avatar>
    </v-btn>
    <v-btn icon title="Logout" @click="handleLogOut">
        <v-icon>exit_to_app</v-icon>
    </v-btn>
</v-toolbar>
</template>

<script>
export default {
    data() {
        return {
            basicImg: 'https://cdn.itviec.com/employers/vccorp/logo/social/pY59TrN7PQff72x8HnEjkUdN/vccorp-logo.PNG'
        }
    },

    props: {
        value: {
            type: Object
        }
    },
    methods: {
        handleLogOut() {
            window.location.href = `${process.env.VUE_APP_AUTH_URL}/logout?service=${process.env.VUE_APP_DASHBOARD_URL}`
        }
    },
}
</script>

<style scoped>

</style>
