<template>
  <v-app>
    <v-content>
      <v-container fluid fill-height>
        <v-flex xs12 sm3  v-for="bsn in negocios" :key="bsn._id">
          <v-card
              class="mx-auto"
              max-width="344"
          >
            <v-img
                :src="bsn.imagen"
                height="200px"
            ></v-img>
            <a href="/vendedor">
              <v-card-title>
                {{ bsn.nombre_negocio }}
              </v-card-title>
            </a>

            <v-card-subtitle>
              {{ bsn.hora_atencion }}<br>{{bsn.direccion}}
            </v-card-subtitle>

            <v-card-actions>
              <v-btn
                  color="orange lighten-2"
                  text
              >
                Explore
              </v-btn>

              <v-spacer></v-spacer>

              <v-btn
                  icon
                  @click="show = !show"
              >
                <v-icon>{{ show ? 'mdi-chevron-up' : 'mdi-chevron-down' }}</v-icon>
              </v-btn>
            </v-card-actions>

            <v-expand-transition>
              <div v-show="show">
                <v-divider></v-divider>

                <v-card-text>
                  {{bsn.descripcion}}
                </v-card-text>
              </div>
            </v-expand-transition>
          </v-card>
          <!--<v-card class="ma-3">
            <v-img
                :src="bsn.img"
                aspect-ratio="1"
            ></v-img>

            <v-card-title primary-title>
              <div>
                <h3 class="headline mb-0">
                  {{bsn.nombre_negocio}}
                </h3>
                <div>
                  <p>
                    {{bsn.descripcion}}
                  </p>
                </div>
              </div>
            </v-card-title>
            <v-card-actions>
              <v-btn color="purple" dark>Share</v-btn>
              <v-btn color="purple" dark>Explore</v-btn>
            </v-card-actions>
          </v-card>-->
        </v-flex>
      </v-container>
    </v-content>
    <v-footer
        dark
        padless
    >
      <v-card
          flat
          tile
          class="indigo lighten-1 white--text text-center"
      >
        <v-card-text>
          <v-btn
              v-for="icon in icons"
              :key="icon"
              class="mx-4 white--text"
              icon
          >
            <v-icon size="24px">
              {{ icon }}
            </v-icon>
          </v-btn>
        </v-card-text>

        <v-card-text class="white--text pt-0">
          Phasellus feugiat arcu sapien, et iaculis ipsum elementum sit amet. Mauris cursus commodo interdum. Praesent ut risus eget metus luctus accumsan id ultrices nunc. Sed at orci sed massa consectetur dignissim a sit amet dui. Duis commodo vitae velit et faucibus. Morbi vehicula lacinia malesuada. Nulla placerat augue vel ipsum ultrices, cursus iaculis dui sollicitudin. Vestibulum eu ipsum vel diam elementum tempor vel ut orci. Orci varius natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus.
        </v-card-text>

        <v-divider></v-divider>

        <v-card-text class="white--text">
          {{ new Date().getFullYear() }} — <strong>TechFind</strong>
        </v-card-text>
      </v-card>
    </v-footer>
  </v-app>
</template>
<script>
import axios from "axios";

export default {
  async created(){
    const response = await axios.get('http://localhost:8000/negocios/vue');
    this.negocios = response.data
  },
  data () {
    return {
      element:[
        {img:'https://i1.wp.com/decorashopsmadrid.com/wp-content/uploads/2018/04/Consejos-para-decorar-una-tienda-de-tecnolog%C3%ADa-e1523026451497.jpg',title:'Nova center',description:'Lorem ipsum dolor sit amet consectetur adipisicing elit. Nesciunt vero corporis incidunt saepe qui commodi quasi neque veniam quam, aspernatur est beatae maxime animi sed reiciendis mollitia ducimus veritatis repellendus?'},
        {img:'https://playersoflife.com/wp-content/uploads/2021/08/PRINCIPAL-Samsung-Store-Torreon-POL.jpg',title:'Samsung Store',description:'Lorem ipsum dolor sit amet consectetur adipisicing elit. Nesciunt vero corporis incidunt saepe qui commodi quasi neque veniam quam, aspernatur est beatae maxime animi sed reiciendis mollitia ducimus veritatis repellendus?'},
        {img:'https://upload.wikimedia.org/wikipedia/commons/thumb/1/11/Xiaomi_Store_Portugal.jpg/640px-Xiaomi_Store_Portugal.jpg',title:'Mi Cell Store',description:'Lorem ipsum dolor sit amet consectetur adipisicing elit. Nesciunt vero corporis incidunt saepe qui commodi quasi neque veniam quam, aspernatur est beatae maxime animi sed reiciendis mollitia ducimus veritatis repellendus?'},
      ],
      icons: [
        'mdi-facebook',
        'mdi-twitter',
        'mdi-linkedin',
        'mdi-instagram',
      ],
      negocios: [],
      show: false,
    }
  },
}
</script>

