<template>
  <v-container class="fill-height d-flex align-center">
    <v-card
      class="mx-auto rounded-lg d-flex flex-column justify-space-between"
      height="720"
      width="100%"
    >
      <v-card-title class="text-h6 font-weight-regular justify-space-between" style="padding: 0; height: 35px;">
        <v-toolbar app class="px-4 align-start" style="height: 35px;">
            <v-toolbar-items class="hidden-xs-only align-center" style="height: 35px;">
            <v-btn @click="step = 1" tag="span" style="cursor: pointer; width: 200px; height: 35px;" class="title d-flex">
              <BsWindow />
              <p dark class="text-body-1 font-weight-light ml-2">Portafólio de Proyectos</p>
            </v-btn>
          </v-toolbar-items>
          <v-spacer></v-spacer>
          <v-toolbar-items class="hidden-xs-only align-center" style="height: 35px;">
            <p class="text-disabled text-body-1 font-weight-light">Desarrollador Frontend</p>
          </v-toolbar-items>
          <v-spacer></v-spacer>
          <v-toolbar-items class="hidden-xs-only align-center" style="height: 35px;">
            <FaRegWindowMaximize />
            <BxWindowClose />
          </v-toolbar-items>
        </v-toolbar>
      </v-card-title>
      <v-layout class="flex-column">
        <v-navigation-drawer
          width="300"
          location="left"
          app="false"
          permanent
          >
          <template v-slot:prepend>
            <div class="d-flex mt-2">
              <v-list-item
                class="pr-0"
                prepend-avatar="@/assets/profile-image.jpg"
              ></v-list-item>
              <div>
                <p class="text-button" style="line-height: 1.3;">
                  Juan Pablo Torrilla Picerno
                </p>
                <div class="py-0 px-0 d-flex align-center">
                  <p class="text-caption text-disabled mr-2">Disponible para trabajar</p>
                  <AdArmrecording color="lime"/>
                </div>
                
              </div>
            </div>
            <v-divider></v-divider>
          </template>

          <v-divider></v-divider>
          <v-card>
            <v-card-title>
              Menu
            </v-card-title>
            <v-list density="compact" nav>
              <v-list-item prepend-icon="mdi-home-city" title="Home" value="home" @click="step = 1"></v-list-item>
              <v-list-item prepend-icon="mdi-account" title="My Account" value="account" @click="step = 2"></v-list-item>
              <v-list-item prepend-icon="mdi-account-group-outline" title="Users" value="users" @click="step = 3"></v-list-item>
            </v-list>
          </v-card>
        </v-navigation-drawer>
        <v-col style="min-width: 300px; max-width: 300px;"></v-col>
        <v-window v-model="step" grid-list-md style="overflow-y: auto; height: 100%;">
          <v-window-item :value="1" row wrap>
          <v-row>
              <v-col cols="3"></v-col>
              <v-col>
                <v-row no-gutters class="justify-center mt-12">
                  <div style="width: 350px; height: 200px;" class="rounded-circle overflow-hidden">
                    <img style="width: -webkit-fill-available; filter: drop-shadow(green 1px 6px 19px);;" src="@/assets/Sin título.png">
                  </img></div>
                  <v-col class="d-flex flex-column mt-12 justify-center">
                    <p class="text-h4">Hola, soy Juan Pablo</p>
                    <p class="text-body-1">Desarrollador Frontend</p>
                  </v-col>
                  <p class="text-body-1 ml-12 mt-10">
                    Me encuentro en búsqueda permamente de desafíos en el mundo de la programación que me permitan desarrollar mis habilidades y crear herramientas únicas para cada cliente.
                    Soy una persona responsable y comprometida con mis proyectos, con experiecia en el liderazgo de equipos y la gestión de la calidad.
                  </p>
                </v-row>
              </v-col>
            </v-row>
          </v-window-item>

          <v-window-item :value="2">
            <v-row>
              <v-col style="min-width:300px"></v-col>
              <v-col>
                <v-row no-gutters class="justify-center">
                  <p class="text-h5 mt-3">Formación</p>
                </v-row>
                <v-row no-gutters wrap>
                  <v-sheet v-for="estudio in formacion" :key="estudio.title" class="d-flex flex-column items-center align-center" >
                    <v-sheet>
                      <v-card >
                        <p class="text-subtitle-1 text-center">{{estudio.title}}</p>
                      <v-img :src="estudio.img" style="border-radius: 50%;" cover></v-img>
                      <v-card-actions>
                        <a :href="estudio.link" target="_blank"> {{estudio.ente}}</a>
                      </v-card-actions>
                      </v-card>
                      
                    </v-sheet>
                  </v-sheet>
                </v-row>
                <v-divider></v-divider>
                <v-row no-gutters class="d-flex justify-center">
                  <p class="text-h5 mt-3">Tecnologías</p>
                </v-row>
                <v-container fluid>
                  <v-layout row >
                    <v-flex v-for="tecnologia in tecnologias" :key="tecnologia.title" class="d-flex items-center align-center">
                      <v-sheet class="border rounded pa-2 d-flex align-center" style="height: 75px; width: 58px;">
                        <v-img :src="tecnologia.img" width="40"cover>
                      </v-img></v-sheet>   
                    </v-flex>
              </v-layout>
                </v-container>  
              </v-col>
            </v-row>
            
          </v-window-item>

          <v-window-item :value="3">
            <div class="pa-4 text-center">
              <v-img
                class="mb-4"
                height="128"
                src="https://cdn.vuetifyjs.com/images/logos/v.svg"
                contain
              ></v-img>
              <h3 class="text-h6 font-weight-light mb-2">
                Welcome to Vuetify
              </h3>
              <span class="text-caption text-grey">Thanks for signing up!</span>
            </div>
          </v-window-item>
        </v-window>
     </v-layout>
      <v-divider></v-divider>

      <v-card-actions>
        <v-btn
          v-if="step > 1"
          variant="text"
          @click="step--"
        >
          Back
        </v-btn>
        <v-spacer></v-spacer>
        <v-btn
          v-if="step < 3"
          color="primary"
          variant="flat"
          @click="step++"
        >
          Next
        </v-btn>
      </v-card-actions>
      
    </v-card>
  </v-container>
</template>
<script>
  export default {
    data: () => ({
      step: 1,
      appTitle: 'Awesome App',
      sidebar: false,
      menuItems: [
          { title: 'Sobre mí', path: '/home', icon: 'home' },
          { title: 'Skills', path: '/signup', icon: 'face' },
          { title: 'Proyectos', path: '/signin', icon: 'lock_open' },
          { title: 'Contacto', path: '/signup', icon: 'face' },
      ],
      open: ['Users'],
      admins: [
        ['Sobre mí', 'mdi-account-multiple-outline'],
        ['Skills', 'mdi-cog-outline'],
        ['Proyectos', 'mdi-folder-open-outline'],
        ['Contacto', 'mdi-email-outline'],
      ],
      formacion: [
        {title: 'Frontend', link: 'https://app.aluracursos.com/user/juan1309/fullCertificate/545282cd7645382a76250c5895a09f41', img: "/src/assets/one.png", ente: 'Alura'},
        ], 
      tecnologias: [
        {title: 'HTML', link: 'https://www.linkedin.com/in/juanpablo-torrilla-picerno/', img: "/src/assets/html-5.svg", ente: 'Alura'},
        {title: 'CSS', link: 'https://www.linkedin.com/in/juanpablo-torrilla-picerno/', img: "/src/assets/css-3.svg", ente: 'Alura'},
        {title: 'Javascript', link: 'https://www.linkedin.com/in/juanpablo-torrilla-picerno/', img: "/src/assets/javascript.svg", ente: 'Alura'},
        {title: 'Vue', link: 'https://www.linkedin.com/in/juanpablo-torrilla-picerno/', img: "/src/assets/vue.svg", ente: 'Alura'},
        {title: 'Vuetify', link: 'https://www.linkedin.com/in/juanpablo-torrilla-picerno/', img: "/src/assets/vuetifyjs.svg", ente: 'Alura'},
        {title: 'Git', link: 'https://www.linkedin.com/in/juanpablo-torrilla-picerno/', img: "/src/assets/git-icon.svg", ente: 'Alura'},
        {title: 'Github', link: 'https://www.linkedin.com/in/juanpablo-torrilla-picerno/', img: "/src/assets/github-icon.svg", ente: 'Alura'},
        {title: 'Gitlab', link: 'https://www.linkedin.com/in/juanpablo-torrilla-picerno/', img: "/src/assets/gitlab.svg", ente: 'Alura'},
        {title: 'Bootstrap', link: 'https://www.linkedin.com/in/juanpablo-torrilla-picerno/', img: "/src/assets/bootstrap.svg", ente: 'Alura'},
        {title: 'Vite', link: 'https://www.linkedin.com/in/juanpablo-torrilla-picerno/', img: "/src/assets/vite.svg", ente: 'Alura'},
        {title: 'Node', link: 'https://www.linkedin.com/in/juanpablo-torrilla-picerno/', img: "/src/assets/nodejs.svg", ente: 'Alura'},
        {title: 'Python', link: 'https://www.linkedin.com/in/juanpablo-torrilla-picerno/', img: "/src/assets/python.svg", ente: 'Alura'},
        {title: 'Django', link: 'https://www.linkedin.com/in/juanpablo-torrilla-picerno/', img: "/src/assets/django.svg", ente: 'Alura'},
        {title: 'Java', link: 'https://www.linkedin.com/in/juanpablo-torrilla-picerno/', img: "/src/assets/java.svg", ente: 'Alura'},

        
      ],
    }
  ),

    methods: {
      home(){
        this.step = 1
      },
    },
    computed: {
      currentTitle () {
        switch (this.step) {
          case 1: return 'Sign-up'
          case 2: return 'Create a password'
          default: return 'Account created'
        }
      },
    },
  }
</script>
