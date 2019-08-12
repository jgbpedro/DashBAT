<template lang="pug">
  div.container
    h1.text-secondary Users 
      i.fa.fa-user
    table.table.table-sripped
      tr
        th Name
        th E-mail
        th Password
        th Youtube
        th Deezer
        th Spotify
      tr(v-for="user of users")
        td {{user.firstName}}
        td {{user.email}}
        td {{user.password}}
        td.text-left
          check(:paramToCheck="user.analytics.youtube.subscribe", :msg="'Subscribe'")
          check(:paramToCheck="user.analytics.youtube.likedAll", :msg="'Liked'")
          check(:paramToCheck="user.analytics.youtube.comment", :msg="'Comment'")
        td.text-left
          check(:paramToCheck="user.analytics.deezer.follow", :msg="'Follow'")
          check(:paramToCheck="user.analytics.deezer.likedAll", :msg="'Liked'")
          check(:paramToCheck="user.analytics.deezer.comment", :msg="'Comment'")
          check(:paramToCheck="user.analytics.deezer.listen.qty ? true : false", :msg="'Listen: '+user.analytics.deezer.listen.qty")
          div Last Updated: {{user.analytics.deezer.lastUpdate}}
        td.text-left
          check(:paramToCheck="user.analytics.spotify.follow", :msg="'Follow'")
          check(:paramToCheck="user.analytics.spotify.likedAll", :msg="'Liked'")
          check(:paramToCheck="user.analytics.spotify.comment", :msg="'Comment'")
          check(:paramToCheck="user.analytics.spotify.listen.qty ? true : false", :msg="'Listen: '+user.analytics.spotify.listen.qty")
          div Last Updated: {{user.analytics.spotify.lastUpdate}}
</template>

<script>
import Check from "./Check";

export default {
  name: "Users",
  props: {
    msg: String
  },
  components: {
    Check
  },
  data() {
    return {
      users: [
        {
          firstName: "Guilherme",
          lastName: "Pedro",
          email: "jgbpedro@bol.com",
          insta: "",
          password: "000000",
          analytics: {
            youtube: {
              subscribe: false,
              likedAll: false,
              comment: false
            },
            spotify: {
              follow: false,
              likedAll: true,
              listen: {
                qty: 0
              },
              relation: [],
              lastUpdate: ""
            },
            deezer: {
              follow: false,
              likedAll: true,
              listen: {
                qty: 0
              },
              relation: [],
              lastUpdate: "20/01/2019"
            }
          }
        },
        {
          firstName: "José",
          lastName: "Pedro",
          email: "joz@bol.com",
          insta: "",
          password: "123456",
          analytics: {
            youtube: {
              subscribe: false,
              likedAll: false,
              comment: false
            },
            spotify: {
              follow: false,
              likedAll: true,
              listen: {
                qty: 0
              },
              relation: [],
              lastUpdate: ""
            },
            deezer: {
              follow: false,
              likedAll: true,
              listen: {
                qty: 0
              },
              relation: [],
              lastUpdate: ""
            }
          }
        },
        {
          firstName: "Pedro",
          lastName: "Gui",
          email: "pedro@bol.com",
          insta: "",
          password: "111222",
          analytics: {
            youtube: {
              subscribe: true,
              likedAll: true,
              comment: false
            },
            spotify: {
              follow: true,
              likedAll: true,
              listen: {
                qty: 1
              },
              relation: [],
              lastUpdate: ""
            },
            deezer: {
              follow: true,
              likedAll: true,
              listen: {
                qty: 3
              },
              relation: [],
              lastUpdate: ""
            }
          }
        }
      ]
    };
  }
};
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
* {
  /* font-size: 10px; */
}
</style>
