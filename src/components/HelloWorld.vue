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
          div
            span Subscribed 
            i.fa.fa-close.text-success(v-if="user.analytics.youtube.subscribe")
            i.fa.fa-close.text-danger(v-else) 
          div
            span Liked 
            i.fa.fa-close.text-success(v-if="user.analytics.youtube.likedAll")
            i.fa.fa-close.text-danger(v-else) 
          div Comment 
            i.fa.fa-close.text-success(v-if="user.analytics.youtube.comment")
            i.fa.fa-close.text-danger(v-else)
          //div Last Updated: {{user.analytics.youtube.lastUpdate}}
        td.text-left
          div Subscribe
          div Liked
          div Listen
          div Last Updated
        td.text-left
          div Subscribe
          div Liked
          div Listen
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
