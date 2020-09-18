<template>
  <v-app>
    <v-app-bar app clipped-left>
      <v-app-bar-nav-icon />
      <v-icon class="mx-4" large>mdi-video</v-icon>
      <v-toolbar-title class="align-center">
        <span class="title">videokod</span>
      </v-toolbar-title>
      <v-spacer />
      <v-text-field
        class="mt-6"
        solo
        placeholder="ara..."
        single-line
        append-icon="mdi-magnify"
        color="white"
      />
      <v-spacer />
      <v-btn class="ml-0" icon>
        <v-icon>mdi-apps</v-icon>
      </v-btn>
      <v-btn class="ma-2" icon>
        <v-icon>mdi-bell</v-icon>
      </v-btn>
      <div>
        <v-menu 
        v-model="menu" 
        :close-on-content-click="false"
        :nudge-width="250"
        offset-x
        >
          <template v-slot:activator="{on}">
            <v-avatar size="40">
              <img v-on="on" src="../src/assets/ironman.png"/>
            </v-avatar>
          </template>
          <v-card>
            <v-list>
              <v-list-item>
                <v-list-item-avatar></v-list-item-avatar>
                <v-list-item-content>
                  <v-list-item-title>IRON MAN</v-list-item-title>
                  <v-list-item-subtitle>Tony STARK</v-list-item-subtitle>
                </v-list-item-content>
              </v-list-item>
            </v-list>
            <v-divider />
            <v-list>
              <v-list-item>
                <v-list-item-action>
                  <v-icon>mdi-cog</v-icon>
                </v-list-item-action>
                <v-list-item-title>ayarlar</v-list-item-title>
              </v-list-item>
            </v-list>
            <v-list>
              <v-list-item>
                <v-list-item-action>
                  <v-switch v-model="theme" color="purple" />
                </v-list-item-action>
                <v-list-item-title>dark</v-list-item-title>
              </v-list-item>
            </v-list>
            <v-card-actions>
              <v-spacer />
              <v-btn color="primary" text @click="menu=false">çıkış yap</v-btn>
            </v-card-actions>
          </v-card>
        </v-menu>
      </div>
    </v-app-bar>
    <v-content>
      <v-container>
        <v-row class="mb-4">
          <v-col v-for="(item,index) in 200" :key="index">
            text {{index}}
          </v-col>
        </v-row>
      </v-container>
    </v-content>
  </v-app>
</template>

<script>
export default {
  name: "App",

  components: {},

  data: () => ({
    menu : false,
    theme : true,
  }),
};
</script>
