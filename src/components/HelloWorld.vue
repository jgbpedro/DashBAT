<template lang="pug">
  div.container
    h1.text-secondary Users 
      i.fa.fa-user
    table.table.table-sripped
      tr
        th Nome
        th E-mail
        th Instagram
        th Senha
        th Youtube
        th Deezer
        th Spotify
      tr(v-for="user of users")
        td {{user.firstName}}
        td {{user.email}}
        td {{user.insta || '-'}}
        td {{user.password}}
        td.text-left
          div.text-success(v-if="user.analytics.youtube.subscribe") Subscribed
          div.text-danger(v-else="user.analytics.youtube.subscribe") Not Subscribed
          div Liked
          div Comment 
          div Last Updated
        td.text-left
          div Subscribe
          div Liked
          div Comment 
          div Last Updated
        td.text-left
          div Subscribe
          div Liked
          div Comment 
          div Last Updated    
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    msg: String
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
              listen: {
                qty: 0
              },
              relation: [],
              lastUpdate: ""
            },
            deezer: {
              follow: false,
              listen: {
                qty: 0
              },
              relation: [],
              lastUpdate: ""
            }
          }
        },
        {
          firstName: "José",
          lastName: "Pedro",
          email: "pedro@bol.com",
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
              listen: {
                qty: 0
              },
              relation: [],
              lastUpdate: ""
            },
            deezer: {
              follow: false,
              listen: {
                qty: 0
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
<style>
</style>
