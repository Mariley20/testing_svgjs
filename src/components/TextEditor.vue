<template>
  <div class="position-text-svg">
    <p class="mb-1 text-center text-sm-left subtitle-2">
     Editar texto
    </p>
    <v-card>
      <v-toolbar
        dense
        flat
      >
        <v-select
          v-model="dataTextSvg.size"
          menu-props="bottom"
          hint="Select font"
          solo
          class="mr-1 text-small"
          dense
          :items="fontSizes"
          hide-details
          append-icon
          @change="sendDataTextSvg"
        />
        <v-select
          v-model="dataTextSvg.lineSpacing"
          dense
          class="mr-1 text-small"
          solo
          :items="linesSpacings"
          hide-details
          append-icon
          @change="sendDataTextSvg"
        />
        <v-select
          v-model="dataTextSvg.fontName"
          dense
          class="mr-1 text-small"
          solo
          :items="fontNames"
          hide-details
          background-color="white"
          append-icon
          @change="sendDataTextSvg"
        />
        <v-btn-toggle
          color="primary"
          dense
          multiple
          @change="sendDataTextSvg"
        >
          <v-btn
            v-model="dataTextSvg.bold"
            text
            @click="dataTextSvg.bold=dataTextSvg.bold"
          >
            <v-icon small>
              mdi-format-bold
            </v-icon>
          </v-btn>
          <v-menu offset-y>
            <template v-slot:activator="{ on, attrs }">
              <v-btn
                slot="activator"
                text
                v-bind="attrs"
                color="primary"
                dark
                v-on="on"
              >
                <v-icon small>
                  mdi-format-color-text
                </v-icon>
              </v-btn>
            </template>
            <v-color-picker
              v-model="dataTextSvg.color"
              class="my-color-picker"
              canvas-height="72"
              width="250px"
              mode="hexa"
              hide-mode-switch
            />
          </v-menu>
          <v-menu offset-y>
            <template v-slot:activator="{ on, attrs }">
              <v-btn
                slot="activator"
                text
                v-bind="attrs"
                color="primary"
                dark
                v-on="on"
              >
                <v-icon small>
                  mdi-format-color-fill
                </v-icon>
              </v-btn>
            </template>
            <v-color-picker
              v-model="dataTextSvg.backgroundColor"
              class="my-color-picker"
              canvas-height="72"
              width="250px"
              mode="hexa"
              hide-mode-switch
            />
          </v-menu>
        </v-btn-toggle>
      <!-- <v-btn
            depressed
            class="pa-2"
            @click="clearTextEditorSvg"
            small
          ><v-icon small>mdi-format-clear</v-icon>
          </v-btn> -->
      </v-toolbar>

      <v-textarea
        v-model="dataTextSvg.text"
        clearable
        clear-icon="mdi-close-circle"
        height="145"
        outlined
        rows="4"
        background-color="white"
        no-resize
        counter
        hide-details
        maxlength="50"
        @click:clear="clearTextEditorSvg"
        @input="sendDataTextSvg"
      />
    </v-card>
    <v-card
      class="mt-3"
    >
      <v-toolbar
        dense
        flat
      >
        <span class="caption mr-3 font-weight-black">Personaliza el % de descuento:</span>

        <v-select
          v-model="dataTextSvg.percentage"
          dense
          class="mr-1 text-small perncetage-btn"
          solo
          :items="percentages"
          hide-details
          background-color="white"
          append-icon
          @change="sendDataTextSvg"
        />
      </v-toolbar>
    </v-card>
  </div>
</template>

<script>
export default {
  props: {

  },
  data: function () {
    return {
      linesSpacings: [0, 1, 2, 3],
      percentages: [5, 10, 15, 20, 25, 30, 35, 40, 45, 50, 55, 60],
      lineSpacing: 0,
      linesSpacing: null,
      fontSizes: ['Extra Small', 'Small', 'Normal', 'Large', 'Extra Large'],
      fontNames: ['Arial', 'Miso', 'Raleway'],
      fontSize: 64,
      mode: 'hsla',
      modes: ['hsla', 'rgba', 'hexa'],
      dataTextSvg: {
        bold: false,
        backgroundColor: '#FF0000',
        size: 'Normal',
        fontName: 'Arial',
        lineSpacing: 0,
        color: '#FFFFFFFF',
        text: '',
        percentage: '10'
      }
    }
  },
  computed: {
  },
  watch: {

  },
  created () {

  },
  methods: {
    sendDataTextSvg () {
      this.$emit('get:dataTextSvg', this.dataTextSvg)
    },
    clearTextEditorSvg () {
      this.dataTextSvg.text = ''
      this.dataTextSvg.bold = ''
      this.dataTextSvg.color = '#FFFFFFFF'
      this.dataTextSvg.backgroundColor = `${this.secondaryColor}FF`
      this.dataTextSvg.lineSpacing = 0
      this.dataTextSvg.size = 'Normal'
      this.dataTextSvg.fontName = 'Miso'
      this.dataTextSvg.percentage = 10
    }
  }
}
</script>

<style lang="scss" scoped>

.position-text-svg {
  max-width: 324px;
  &--size {
    font-size: 10px;
  }
}
.perncetage-btn {
  max-width: 70px;
}
</style>
