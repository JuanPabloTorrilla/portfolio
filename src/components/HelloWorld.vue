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
              <p dark class="text-body-1 font-weight-light ml-2">Portafolio de Proyectos</p>
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
                  <AdArmrecording color="lime" style="filter: drop-shadow(0px 0px 5px lime);"/>
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
              <v-list-item prepend-icon="mdi-folder-account" title="Sobre mí" value="home" @click="step = 1"></v-list-item>
              <v-list-item prepend-icon="mdi-folder-cog" title="Skills" value="account" @click="step = 2"></v-list-item>
              <v-list-item prepend-icon="mdi-folder-multiple-image" title="Proyectos" value="users" @click="step = 3"></v-list-item>
            </v-list>
          </v-card>
          <v-divider></v-divider>
          <v-card>
            <v-card-title>
              Contacto
            </v-card-title>
            <v-list density="compact" nav>
              <v-list-item prepend-icon="mdi-email" title="Escríbeme" value="home" @click="step = 4"></v-list-item>
              <v-speed-dial
                location="right center"
                transition="scale-transition"
                style="width: webkit-fill-available;"
              >
                <template v-slot:activator="{ props: activatorProps }">
                  <v-list-item prepend-icon="mdi-folder-network" title="Redes" v-bind="activatorProps"></v-list-item>
                </template>
                <v-sheet style="background-color: transparent; box-shadow: none; filter: drop-shadow(0px 0px 5px white);">
                  <a v-for="red in redes" :key=red.title :href=red.link target="_blank"><v-btn :icon=red.icon @click="red.link"></v-btn></a>
                  <v-btn icon="$error"></v-btn>
                </v-sheet>
                
              </v-speed-dial>
              
            </v-list>
          </v-card>
        </v-navigation-drawer>
        <v-col style="min-width: 300px; max-width: 300px; height: 100%;">
        </v-col>
        <v-window v-model="step" grid-list-md style="overflow-y: auto; height: 100%;">
          <v-window-item :value="1" row wrap>
          <v-row>
              <v-col cols="3"></v-col>
              <v-col>
                <v-row no-gutters class="justify-center mt-12">
                  <div style="width: 350px; height: 200px;" class="rounded-circle overflow-hidden">
                    <img style="width: -webkit-fill-available; filter: drop-shadow(white 1px 6px 19px);;" src="@/assets/Sin título.png">
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
              <v-col style="min-width:300px; max-width: 310px;"></v-col>
              <v-col>
                <v-row no-gutters class="justify-center">
                  <p class="text-h5 mt-3">Formación</p>
                </v-row>
                <v-row no-gutters wrap class="pl-4 pb-2">
                  <v-card v-for="estudio in formacion" :key="estudio.title">
                    <v-sheet class="border rounded pa-2 d-flex flex-column items-center align-center">
                      <p class="text-subtitle-1 text-center">{{estudio.title}}</p>
                      <v-sheet><v-img :src=estudio.img style="border-radius: 50%; width: 80px;"></v-img></v-sheet>
                      <v-card-actions>
                        <a :href="estudio.link" target="_blank"> {{estudio.ente}}</a>
                      </v-card-actions>
                    </v-sheet>
                  </v-card>
                </v-row>
                <v-divider></v-divider>
                <v-row no-gutters class="d-flex justify-center">
                  <p class="text-h5 mt-3">Tecnologías</p>
                </v-row>
                <v-container fluid>
                  <v-layout row class="d-flex flex-wrap ga-1 pb-2">
                    <v-card v-for="tecnologia in tecnologias" :key="tecnologia.title" class="d-flex items-center align-center">
                      <v-sheet class="border rounded pa-2 d-flex align-center" style="height: 105px; width: 78px;">
                        <v-img :src="tecnologia.img" width="40"cover>
                      </v-img></v-sheet>   
                    </v-card>
              </v-layout>
                </v-container>  
              </v-col>
            </v-row>
            
          </v-window-item>

          <v-window-item :value="3">
            <v-container fluid class="d-flex">
              <v-col style="min-width:300px; max-width: 310px;"></v-col>
              <v-col>
                <v-row no-gutters class="justify-center mb-3 pb-3">
                  <p class="text-h5 mt-3">Proyectos</p>
                </v-row>
                <v-row no-gutters wrap class="pl-4 pb-2 ga-2">
                  <v-card v-for="proyecto in proyectos" :key="proyecto.title">
                    <v-sheet class="border pa-2 d-flex flex-column items-center align-center justify-space-between" style="border-radius: 30px; background-color: #83e9ff63; height: 268px;">
                      <p class="text-subtitle-1 text-center">{{proyecto.title}}</p>
                      <v-sheet><v-img :src="proyecto.img" style="width: 220px;"></v-img></v-sheet>
                      <v-card-actions>
                        <a :href="proyecto.link" target="_blank"> ver online </a>
                      </v-card-actions>
                    </v-sheet>
                  </v-card>
                </v-row>
               
              </v-col>
            </v-container>
          </v-window-item>
          <v-window-item :value="4">
            <v-container fluid class="d-flex">
              <v-col style="min-width:300px; max-width: 310px;"></v-col>
              <v-col>
                <v-row no-gutters class="justify-center mb-3 pb-3">
                  <p class="text-h5 mt-3">Contacto</p>
                </v-row>
                <v-row no-gutters wrap class="pl-4 pb-2 justify-center">
                  <v-card style=" box-shadow: 17px 19px 7px -5px rgb(0 0 0 / 44%)" width="500" class="bg-grey-darken-3">
                    <v-sheet class="mx-auto">
                      <v-form fast-fail @submit.prevent>
                        <v-text-field
                          v-model="nombre"
                          :rules="firstNameRules"
                          label="Nombre"
                        ></v-text-field>

                        <v-text-field
                          v-model="email"
                          :rules="emailRules"
                          label="E-mail"
                          type="email"
                        ></v-text-field>

                        <v-textarea 
                        v-model="message"
                        :rules="messageRules"
                        label="Cuéntame sobre tu proyecto"></v-textarea>

                        <v-btn class="mt-2" type="submit" block>Submit</v-btn>
                      </v-form>
                    </v-sheet>
                  </v-card>
                </v-row>
              </v-col>
            </v-container>
          </v-window-item>

        </v-window>
          
     </v-layout>
      <v-divider></v-divider>

      <v-card-actions class="justify-center ">
        <p class="text-caption text-disabled">Desarrollado por Juan Pablo Torrilla Picerno</p>
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
          { title: 'Sobre mí', path: '/home', icon: 'face' },
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
        {title: 'Frontend', link: 'https://app.aluracursos.com/user/juan1309/fullCertificate/545282cd7645382a76250c5895a09f41', img: "@/assets/one.png", ente: 'Alura'},
        ], 
      tecnologias: [
        {title: 'HTML', link: 'https://www.linkedin.com/in/juanpablo-torrilla-picerno/', img: "/assets/html-5.svg"},
        {title: 'CSS', link: 'https://www.linkedin.com/in/juanpablo-torrilla-picerno/', img: "@/assets/css-3.svg"},
        {title: 'Javascript', link: 'https://www.linkedin.com/in/juanpablo-torrilla-picerno/', img: "@/assets/javascript.svg"},
        {title: 'Vue', link: 'https://www.linkedin.com/in/juanpablo-torrilla-picerno/', img: "@/assets/vue.svg"},
        {title: 'Vuetify', link: 'https://www.linkedin.com/in/juanpablo-torrilla-picerno/', img: "@/assets/vuetifyjs.svg"},
        {title: 'Git', link: 'https://www.linkedin.com/in/juanpablo-torrilla-picerno/', img: "@/assets/git-icon.svg"},
        {title: 'Github', link: 'https://www.linkedin.com/in/juanpablo-torrilla-picerno/', img: "@/assets/github-icon.svg"},
        {title: 'Gitlab', link: 'https://www.linkedin.com/in/juanpablo-torrilla-picerno/', img: "@/assets/gitlab.svg"},
        {title: 'Bootstrap', link: 'https://www.linkedin.com/in/juanpablo-torrilla-picerno/', img: "@/assets/bootstrap.svg"},
        {title: 'Vite', link: 'https://www.linkedin.com/in/juanpablo-torrilla-picerno/', img: "@/assets/vitejs.svg"},
        {title: 'Node', link: 'https://www.linkedin.com/in/juanpablo-torrilla-picerno/', img: "@/assets/nodejs.svg"},
        {title: 'Python', link: 'https://www.linkedin.com/in/juanpablo-torrilla-picerno/', img: "@/assets/python.svg"},
        {title: 'Django', link: 'https://www.linkedin.com/in/juanpablo-torrilla-picerno/', img: "@/assets/typescript-icon.svg"},
        {title: 'Java', link: 'https://www.linkedin.com/in/juanpablo-torrilla-picerno/', img: "@/assets/java.svg"},

        
      ],
      proyectos: [
        {title: 'Encriptador', link: 'https://juanpablotorrilla.github.io/Alura_ONE-Challenge_1/', img: "@/assets/encriptador.png"},
        {title: 'Ahorcado', link: 'https://juanpablotorrilla.github.io/alura_challenge2/', img: "@/assets/ahorcado.png"},
        {title: 'SGC Management', link: 'https://juanpablotorrilla.github.io/alura_challenge3/', img: "@/assets/sgc.png"},
        {title: 'Game Store', link: 'https://juanpablotorrilla.github.io/alura_challenge4/', img: "@/assets/store.png"},
        {title: 'Gestor de Alumnos', link: 'https://juanpablotorrilla.github.io/alura_challenge5/', img: "@/assets/alumnos.png"},
      ],
      redes: [
        {title: 'Linkedin', link: 'https://www.linkedin.com/in/juanpablotorrilla', icon:"mdi-linkedin"},
        {title: 'Github', link: 'https://www.linkedin.com/in/juanpablo-torrilla-picerno/', icon:"mdi-github"},
        {title: 'Gitlab', link: 'https://www.linkedin.com/in/juanpablo-torrilla-picerno/', icon:"mdi-gitlab"},
      ],

      nombre: '',
      firstNameRules: [
        value => {
          if (value?.length > 3) return true

          return 'First name must be at least 3 characters.'
        },
        value => {
          if (/[^0-9]/.test(value)) return true

          return 'Last name can not contain digits.'
        },
      ],

      email: '',
      emailRules: [
        value => {
          if (/[^@ \t\r\n]+@[^@ \t\r\n]+\.[^@ \t\r\n]+/.test(value)) return true

          return 'E-mail must be valid.'
    }
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
