<template>
  <v-row>
    <v-dialog
      v-model="dialog"
      scrollable
      max-width="400px"
    >
      <template v-slot:activator="{ on, attrs }">
        <v-btn
          color="primary"
          icon
          v-bind="attrs"
          v-on="on"
        >
          <v-icon>mdi-calendar-clock-outline</v-icon>
        </v-btn>
      </template>
      <v-card>
        <v-toolbar
          color="primary"
          dark
        >
          <v-card-actions class="justify-start">
            <v-btn
                icon
                text
                @click="dialog = false, deleteDateTime()"
            >
              <v-icon>mdi-trash-can-outline</v-icon>
            </v-btn>
          </v-card-actions>
          <v-spacer></v-spacer>
          <v-card-title>
              {{title}}
          </v-card-title>
          <v-spacer></v-spacer>
          <v-card-actions class="justify-end">
            <v-btn
                icon
                text
                @click="dialog = false, emitDateTime()"
            >
              <v-icon>mdi-check</v-icon>
            </v-btn>
          </v-card-actions>
        </v-toolbar>
        <v-divider></v-divider>
        <v-checkbox
          v-model="allDay"
          label="終日の予定"
          class="mx-auto"
        ></v-checkbox>
        <v-card-text style="height: 600px;">
            <v-row justify="center" class="mt-3">
                <v-spacer></v-spacer>
                <v-date-picker v-model="picker"></v-date-picker>
                <v-spacer></v-spacer>
            </v-row>
            <v-slide-y-transition>
              <v-row justify="center" v-show="!allDay">
                  <v-spacer></v-spacer>
                  <v-time-picker format="24hr" scrollable v-model="timePicker"></v-time-picker>
                  <v-spacer></v-spacer>
              </v-row>
            </v-slide-y-transition>
        </v-card-text>
      </v-card>
    </v-dialog>
  </v-row>
</template>

<script>
export default {
    props:['title'],
    data () {
      return {
        dialog: false,
        picker:(new Date(Date.now() - (new Date()).getTimezoneOffset() * 60000)).toISOString().substr(0, 10),
        timePicker:'00:00',
        allDay: false
      }
    },
    computed :{
        formatDateTime(){
            const dateTime = `${this.picker} ${this.timePicker}`
            return new Date(dateTime)
        }
    },
    methods:{
        emitDateTime(){
          this.title === '開始日時' ? this.$emit('inputStart', this.formatDateTime) :this.$emit('inputEnd', this.formatDateTime)
          this.deleteDateTime()
        },
        emitAllDay(){
          allDay? this.$emit('emitAllDay'): this.allDay = false
        },
        deleteDateTime(){
          this.picker = (new Date(Date.now() - (new Date()).getTimezoneOffset() * 60000)).toISOString().substr(0, 10)
          this.timePicker = '00:00'
          this.allDay = false
        }
    }
  }
</script>

<style>

</style>