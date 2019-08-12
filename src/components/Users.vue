<template lang="pug">
  div.container
    div.modalToken(v-if="!token")
      div.formModal
        input.token-control.form-control(type="text", placeholder="Insert Token", v-model="dataToken", @input="verifyToken()")

    div.modalUser(v-if="create")
      div.formModal
        form.form
          div.form-group
            input.token-control.form-control(type="text", placeholder="First Name", v-model="user.firstName")  
            input.token-control.form-control.mt-2(type="text", placeholder="Last Name", v-model="user.lastName")  
            input.token-control.form-control.mt-2(type="email", placeholder="E-mail", v-model="user.email")  
            input.token-control.form-control.mt-2(type="text", placeholder="Password", v-model="user.password")  
            input.token-control.form-control.mt-2.success(type="button", value="Submit" @click="addUser()")  

    h1.text-secondary
      small.badge.badge-success {{users.length}} 
      span  Users
      i.fa.fa-plus-circle.pull-right.text-success.mt-2(@click="create = true")
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
          check(:paramToCheck="user.analytics.youtube.subscribe", :msg="'Subscribe'", :toggle="toggle")
          check(:paramToCheck="user.analytics.youtube.likedAll", :msg="'Liked'", :toggle="toggle")
          check(:paramToCheck="user.analytics.youtube.comment", :msg="'Comment'", :toggle="toggle")
        td.text-left
          check(:paramToCheck="user.analytics.deezer.follow", :msg="'Follow'", :toggle="toggle")
          check(:paramToCheck="user.analytics.deezer.likedAll", :msg="'Liked'", :toggle="toggle")
          check(:paramToCheck="user.analytics.deezer.comment", :msg="'Comment'", :toggle="toggle")
          check(:paramToCheck="user.analytics.deezer.listen.qty ? true : false", :msg="'Listen: '+user.analytics.deezer.listen.qty", :toggle="toggle")
          div Last Updated: {{user.analytics.deezer.lastUpdate}}
        td.text-left
          check(:paramToCheck="user.analytics.spotify.follow", :msg="'Follow'", :toggle="toggle")
          check(:paramToCheck="user.analytics.spotify.likedAll", :msg="'Liked'", :toggle="toggle")
          check(:paramToCheck="user.analytics.spotify.comment", :msg="'Comment'", :toggle="toggle")
          check(:paramToCheck="user.analytics.spotify.listen.qty ? true : false", :msg="'Listen: '+user.analytics.spotify.listen.qty", :toggle="toggle")
          div Last Updated: {{user.analytics.spotify.lastUpdate}}
</template>

<script>
import Check from "./Check";

export default {
  props: {
    msg: String
  },
  components: {
    Check
  },
  data() {
    return {
      token: true,
      dataToken: null,
      create: false,
      user: {
        firstName: null,
        lastName: null,
        email: null,
        password: null
      },
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
  },
  methods: {
    verifyToken() {
      console.log("We are verifying...");
      if (this.dataToken === "KHJYES") {
        this.token = true;
      }
    },
    addUser() {
      const user = {
        ...this.user,
        analytics: {
          youtube: {
            subscribe: false,
            likedAll: false,
            comment: false
          },
          spotify: {
            follow: false,
            likedAll: false,
            listen: {
              qty: 0
            },
            relation: [],
            lastUpdate: ""
          },
          deezer: {
            follow: false,
            likedAll: false,
            listen: {
              qty: 0
            },
            relation: [],
            lastUpdate: ""
          }
        }
      };

      this.users.push(user);
      console.log("User added: ", user);

      this.user = {
        firstName: null,
        lastName: null,
        email: null,
        password: null
      };

      this.create = false;
    },
    toggle() {
      console.log("working");
    }
  }
};
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.modalToken,
.modalUser {
  position: fixed;
  width: 100vw;
  height: 100vh;
  background: #8D5AFF;
  opacity: 0.97;
  left: 0;
  top: 0;
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
}
.token-control {
  width: 30vw;
}

.success {
  background: #33CC48;
  color: #fff;
}
</style>
