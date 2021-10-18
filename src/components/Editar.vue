<template>
<div>
    <div class="text-h4 text-center pa-3">
        Editar Usuario
    </div>

    <v-form
    ref="form"
    lazy-validation
    class="pa-7"
  >
    <v-text-field
      v-model="name"
      :counter="10"
      :rules="nameRules"
      label="Name"
      required
    ></v-text-field>

    <v-text-field
      v-model="email"
      :rules="emailRules"
      label="E-mail"
      required
    ></v-text-field>

    <v-btn
      color="yellow lighten-1"
      class="mr-4"
      @click="modificarUsuario"
    >
    <v-icon left>
          mdi-account-edit-outline
      </v-icon>
      Edit User
      
    </v-btn>
    <v-btn
      color="blue"
      class="mr-4"
      @click="goHome"
    >
    <v-icon left>
          mdi-home-variant-outline
      </v-icon>
      Go Home
    </v-btn>
  </v-form>
</div>
    
</template>

<script>
  export default {
    data: () => ({
      name: '',
      nameRules: [
        v => !!v || 'Name is required',
        v => (v && v.length <= 10) || 'Name must be less than 10 characters',
      ],
      email: '',
      emailRules: [
        v => !!v || 'E-mail is required',
        v => /.+@.+\..+/.test(v) || 'E-mail must be valid',
      ],
      usuario:{}
    }),

    methods: {
      goHome () {
        window.location.href('/listar')
      },
      modificarUsuario(){

      },
      obtenerUsuario(){
        console.log(this.idUsuario)
      }
    },
    mounted(){
      this.obtenerUsuario()
    },
    computed:{
      idUsuario:{
        get(){
          return this.$store.state.idUsuario
        }
      }
    }
  }
</script>