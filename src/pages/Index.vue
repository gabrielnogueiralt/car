<template>
  <div>
    <v-app-bar
        app
        color="white"
        height="100"
      >
        <v-avatar
          class="mr-3"
          color="grey lighten-5"
          size="70"
        >
          <v-img
            contain
            max-height="70%"
            src="https://images.unsplash.com/photo-1551150441-649e0b074fe4?ixid=MXwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHw%3D&ixlib=rb-1.2.1&auto=format&fit=crop&w=1350&q=80"
          ></v-img>
        </v-avatar>

        <v-toolbar-title class="font-weight-black headline">
          SID VEÍCULOS
        </v-toolbar-title>
        <v-btn plain>
          <a @click="$vuetify.goTo('#about')">Sobre</a>
        </v-btn>
        <v-btn plain>
          <a @click="$vuetify.goTo('#stock')">Estoque</a>
        </v-btn>
        <v-btn plain>
          <a @click="$vuetify.goTo('#contact')">Contato</a>
        </v-btn>
      </v-app-bar>

      <v-content>
        <section id="hero">
          <v-row no-gutters>
            <v-img
              :min-height="'calc(100vh - ' + $vuetify.application.top + 'px)'"
              src="https://images.unsplash.com/photo-1508974239320-0a029497e820?ixid=MXwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHw%3D&ixlib=rb-1.2.1&auto=format&fit=crop&w=1350&q=80"
            >
              <v-theme-provider dark>
                <v-container fill-height>
                  <v-row
                    align="center"
                    class="white--text mx-auto"
                    justify="center"
                  >
                    <v-col
                      class="white--text text-center"
                      cols="12"
                      tag="h1"
                    >
                      <span
                      :class="[$vuetify.breakpoint.smAndDown ? 'display-1' : 'display-2']"
                        class="font-weight-light"
                      >
                        COMPRE OU VENDA AGORA
                      </span>

                      <br>

                      <span
                        :class="[$vuetify.breakpoint.smAndDown ? 'display-3': 'display-4']"
                        class="font-weight-black"
                      >
                        SEU CARRO
                      </span>

                    </v-col>

                    <v-btn
                      class="align-self-end"
                      fab
                      outlined
                      @click="$vuetify.goTo('#about')"
                    >
                      <v-icon>mdi-chevron-double-down</v-icon>
                    </v-btn>
                  </v-row>
                </v-container>
              </v-theme-provider>
            </v-img>
          </v-row>
        </section>

        <section id="about" ref="about">
          <div class="py-12"></div>

          <v-container class="text-center">
            <h2 class="display-2 font-weight-bold mb-3">SOBRE</h2>

            <v-responsive
              class="mx-auto mb-8"
              width="56"
            >
              <v-divider class="mb-1"></v-divider>

              <v-divider></v-divider>
            </v-responsive>

            <v-responsive
              class="mx-auto title font-weight-light mb-8"
              max-width="720"
            >
              Trabalhamos a mais de 20 anos no mercado de automóveis, sempre buscando as melhores oportunidades para nossos clintes!
            </v-responsive>

            <v-avatar
              class="elevation-12 mb-12"
              size="128"
            >
              <v-img src="https://images.unsplash.com/photo-1518306727298-4c17e1bf6942?ixid=MXwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHw%3D&ixlib=rb-1.2.1&auto=format&fit=crop&w=676&q=80"></v-img>
            </v-avatar>

            <div></div>

            <!-- <v-btn
              color="grey"
              href="https://vuetifyjs.com"
              outlined
              large
            >
              <span class="grey--text text--darken-1 font-weight-bold">
                Vuetify Documentation
              </span>
            </v-btn> -->
          </v-container>

          <div class="py-12"></div>
        </section>

        <section id="stats" ref="stats">
          <v-parallax
            :height="$vuetify.breakpoint.smAndDown ? 700 : 500"
            src="https://images.unsplash.com/photo-1517994112540-009c47ea476b?ixid=MXwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHw%3D&ixlib=rb-1.2.1&auto=format&fit=crop&w=1381&q=80"
          >
            <v-container fill-height>
              <v-row class="mx-auto">
                <v-col
                  v-for="[value, title] of stats"
                  :key="title"
                  cols="12"
                  md="3"
                >
                  <div class="text-center">
                    <div
                      class="display-3 font-weight-black mb-4"
                      v-text="value"
                    ></div>

                    <div
                      class="title font-weight-regular text-uppercase"
                      v-text="title"
                    ></div>
                  </div>
                </v-col>
              </v-row>
            </v-container>
          </v-parallax>
        </section>

        <section id="stock" ref="stock">
          <div class="py-12"></div>

          <v-container>
            <h2 class="display-2 font-weight-bold mb-3 text-uppercase text-center">ESTOQUE</h2>

            <v-responsive
              class="mx-auto mb-12"
              width="56"
            >
              <v-divider class="mb-1"></v-divider>

              <v-divider></v-divider>
            </v-responsive>

            <v-row>
              <v-col
                v-for="({ src, modelo, marca, versao, ano, quilometragem, cor, preco }, i) in articles"
                :key="i"
                cols="12"
                md="4"
              >
                <v-img
                  :src="src"
                  class="mb-4"
                  height="275"
                  max-width="100%"
                ></v-img>

                <h3
                  class="font-weight-black mb-4 text-uppercase"
                >Modelo: {{modelo}}</h3>

                <div
                  class="title font-weight-light mb-5"
                ><b>Marca: </b>{{marca}}</div>
                <div
                  class="title font-weight-light mb-5"
                ><b>Versão: </b>{{versao}}</div>
                <div
                  class="title font-weight-light mb-5"
                ><b>Ano: </b>{{ano}}</div>
                <div
                  class="title font-weight-light mb-5"
                ><b>Quilometragem: </b>{{quilometragem}}</div>
                <div
                  class="title font-weight-light mb-5"
                ><b>Cor: </b>{{cor}}</div>
                <div
                  class="title font-weight-light mb-5"
                ><b>Preço: </b>{{preco}}</div>

                <v-btn
                  class="ml-n4 font-weight-black"
                  text
                >
                  Ver mais detalhes
                </v-btn>
              </v-col>
            </v-row>
          </v-container>

          <div class="py-12"></div>
        </section>
        <section ref="contact">
          <v-sheet
          id="contact"
          color="#333333"
          dark
          tag="section"
          tile
          >
            <div class="py-12"></div>

            <v-container>
              <h2 class="display-2 font-weight-bold mb-3 text-uppercase text-center">ENTRE EM CONTATO</h2>

              <v-responsive
                class="mx-auto mb-12"
                width="56"
              >
                <v-divider class="mb-1"></v-divider>

                <v-divider></v-divider>
              </v-responsive>

              <v-theme-provider light>
                <v-row>
                  <v-col cols="12">
                    <v-text-field
                      flat
                      label="Nome*"
                      solo
                    ></v-text-field>
                  </v-col>

                  <v-col cols="12">
                    <v-text-field
                      flat
                      label="Email*"
                      solo
                    ></v-text-field>
                  </v-col>

                  <v-col cols="12">
                    <v-text-field
                      flat
                      label="Assunto*"
                      solo
                    ></v-text-field>
                  </v-col>

                  <v-col cols="12">
                    <v-textarea
                      flat
                      label="Mensagem*"
                      solo
                    ></v-textarea>
                  </v-col>

                  <v-col
                    class="mx-auto"
                    cols="auto"
                  >
                    <v-btn
                      color="accent"
                      x-large
                    >
                      ENVIAR
                    </v-btn>
                  </v-col>
                </v-row>
              </v-theme-provider>
            </v-container>

            <div class="py-12"></div>
          </v-sheet>
        </section>
        
      </v-content>

      <v-footer
        class="justify-center"
        color="#292929"
        height="100"
      >
        <div class="title font-weight-light grey--text text--lighten-1 text-center">
          &copy; {{ (new Date()).getFullYear() }}
        </div>
      </v-footer>
  </div>
</template>

<script>
  export default {
    name: 'Index',

    data () {
      return {
        articles: [
          {
            src: 'https://images.unsplash.com/photo-1423784346385-c1d4dac9893a?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1950&q=80',
            title: 'Mobile first & Responsive',
            text: 'Phasellus lorem enim, luctus ut velit eget, convallis egestas eros. Sed ornare ligula eget tortor tempor, quis porta tellus dictum.',
          },
          {
            src: 'https://images.unsplash.com/photo-1475938476802-32a7e851dad1?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1950&q=80',
            title: 'Think outside the box',
            text: 'Nam ut leo ipsum. Maecenas pretium aliquam feugiat. Aenean vel tempor est, vitae tincidunt risus. Sed sodales vestibulum nibh.',
          },
          {
            src: 'https://images.unsplash.com/photo-1416339442236-8ceb164046f8?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1892&q=80',
            title: 'Small changes, big difference',
            text: 'Vestibulum in dictum velit, in rhoncus nibh. Maecenas neque libero, interdum a dignissim in, aliquet vitae lectus. Phasellus lorem enim, luctus ut velit eget.',
          },
        ],
        features: [
          {
            icon: 'mdi-account-group-outline',
            title: 'Vibrant Community',
            text: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Iusto cupiditate sint possimus quidem atque harum excepturi nemo velit tempora! Enim inventore fuga, qui ipsum eveniet facilis obcaecati corrupti asperiores nam',
          },
          {
            icon: 'mdi-update',
            title: 'Frequent Updates',
            text: 'Sed ut elementum justo. Suspendisse non justo enim. Vestibulum cursus mauris dui, a luctus ex blandit. Lorem ipsum dolor sit amet consectetur adipisicing elit. qui ipsum eveniet facilis obcaecati corrupti consectetur adipisicing elit.',
          },
          {
            icon: 'mdi-shield-outline',
            title: 'Long-term Support',
            text: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Iusto cupiditate sint possimus quidem atque harum excepturi nemo velit tempora! Enim inventore fuga, qui ipsum eveniet facilis obcaecati corrupti asperiores nam',
          },
        ],
        stats: [
          ['24k', 'Github Stars'],
          ['330+', 'Releases'],
          ['1m', 'Downloads/mo'],
          ['5m', 'Total Downloads'],
        ],
      }
    }
  }
</script>
