<template>
  <v-app>
    <v-navigation-drawer v-model="drawer" app clipped floating temporary>
      <v-list dense>
        <v-row class="ma-2 mb-3">
          <v-icon class="mx-4" large>mdi-video</v-icon>
      <v-toolbar-title class="align-center">
        <span class="title">kebele</span>
      </v-toolbar-title>
        </v-row>
        <v-list-item v-for="(item) in items" :key="item.icon" link>
          <v-list-item-action>
            <v-icon>{{item.icon}}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title>
              {{item.text}}
            </v-list-item-title>
          </v-list-item-content>
            
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-app-bar app clipped-left>
      <v-app-bar-nav-icon @click="drawer=!drawer"/>
      <v-icon class="mx-4" large>mdi-video</v-icon>
      <v-toolbar-title class="align-center">
        <span class="title">kebele</span>
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
          <template v-slot:activator="{ on }">
            <v-avatar size="40">
              <img v-on="on" src="../src/assets/ironman.png" />
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
              <v-btn color="primary" text @click="menu = false"
                >çıkış yap</v-btn
              >
            </v-card-actions>
          </v-card>
        </v-menu>
      </div>
    </v-app-bar>
    <v-main>
      <v-container>
        <v-row class="mb-4">
          <v-col sm="6" md="4" lg="3" xl="2" v-for="(item, index) in 50" :key="index">
            <v-card>
              <v-img heigth="200px" :src="`https://picsum.photos/500/300?images=${(index+1)}`" :lazy-src="`https://picsum.photos/10/5?images=${(index+1)}`" />
              <v-card-subtitle class="">
                number {{item}}
              </v-card-subtitle>
              <v-card-text class="text-primary">
                <div>başlık alanı</div>
                <div>başlık içeriği</div>
              </v-card-text>
              <v-card-actions>
                <v-btn color="orange" text>kaydet</v-btn>
                <v-btn color="orange" text>paylaş</v-btn>
              </v-card-actions>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
export default {
  name: "App",

  components: {},

  data: () => ({
    menu: false,
    theme: false,
    drawer : false,
    items : [
      {icon:"mdi-trending-up", text:"popüler içerik"},
      {icon:"mdi-youtube-subscription", text:"takip"},
      {icon:"mdi-history", text:"geçmiş"},
      {icon:"mdi-playlist-play", text:"play"},
      {icon:"mdi-clock", text:"saat"},
    ]
  }),

  watch: {
    theme:function(next){
      this.$vuetify.theme.dark = next
    }
  },
};
</script>
