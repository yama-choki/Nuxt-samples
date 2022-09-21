<template>
  <div>
    <v-row
      justify="center"
    >
      <v-btn
        color="primary"
        class="ma-2"
        icon
        @click="dialog2 = true"
      >
        <v-icon>mdi-pencil-plus</v-icon>
      </v-btn>

      <v-dialog
        v-model="dialog2"
        max-width="500px"
      >
        <v-card>
            <v-toolbar
                color="primary"
                dark
            >
                <v-card-actions class="justify-start">
                    <v-btn
                        icon
                        text
                        @click="dialog2 = false"
                    >
                        <v-icon>mdi-trash-can-outline</v-icon>
                    </v-btn>
                </v-card-actions>
                <v-spacer></v-spacer>
                <v-card-title>
                    新しい予定
                </v-card-title>
                <v-spacer></v-spacer>
                <v-card-actions class="justify-end">
                    <v-btn
                        icon
                        text
                        @click="dialog2 = false"
                    >
                        <v-icon>mdi-calendar-edit-outline</v-icon>
                    </v-btn>
                </v-card-actions>
            </v-toolbar>

            <v-card-text>
                <div class="text-h2 pa-12">
                    <v-container fluid>
                        <v-text-field
                            v-model="title"
                            counter="10"
                            hint="10文字以内"
                            label="タイトル"
                        ></v-text-field>
                        <v-btn text style="width:100%;">
                            開始　<span>2022年10月10日</span><span>15:00</span>
                        </v-btn>
                        <v-btn text style="width:100%;">
                            終了　<span>2022年10月10日</span><span>16:00</span>
                        </v-btn>
                        <v-textarea
                            clearable
                            clear-icon="mdi-close-circle"
                            label="メモ"
                            counter="200"
                            hint="200文字以内"
                            v-model="memo"
                        ></v-textarea>
                        <v-select
                        :items="select"
                        label="色"
                        item-value="text"
                        ></v-select>
                    </v-container>
                </div>
            </v-card-text>
          <v-card-text>
            <v-btn
              color="primary"
              dark
              @click="dialog3 = !dialog3"
            >
              Open Dialog 3
            </v-btn>
          </v-card-text>
        </v-card>
      </v-dialog>

      <!-- 3つ目のダイアログ　日時入力フォーム -->
      <v-dialog
        v-model="dialog3"
        max-width="800px"
      >
        <v-card>
            <v-toolbar
                color="primary"
                dark
            >
                <v-card-actions class="justify-start">
                    <v-btn
                        icon
                        text
                        @click="dialog3 = false"
                    >
                        <v-icon>mdi-trash-can-outline</v-icon>
                    </v-btn>
                </v-card-actions>
                <v-spacer></v-spacer>
                <v-card-title>
                    予定の日時
                </v-card-title>
                <v-spacer></v-spacer>
                <v-card-actions class="justify-end">
                    <v-btn
                        icon
                        text
                        @click="dialog3 = false"
                    >
                        <v-icon>mdi-check</v-icon>
                    </v-btn>
                </v-card-actions>
            </v-toolbar>

          <v-card-title>
            <v-spacer></v-spacer>
            <span>開始日時</span>
            <v-spacer></v-spacer>
          </v-card-title>
          <v-row justify="center">
            <v-spacer></v-spacer>
            <v-date-picker v-model="minPicker"></v-date-picker>
            <v-spacer></v-spacer>
            <v-time-picker format="24hr" scrollable ></v-time-picker>
            <v-spacer></v-spacer>
          </v-row>

          <v-card-title>
            <v-spacer></v-spacer>
            <span>終了日時</span>
            <v-spacer></v-spacer>
          </v-card-title>
          <v-row justify="center">
            <v-spacer></v-spacer>
            <v-date-picker v-model="maxPicker"></v-date-picker>
            <v-spacer></v-spacer>
            <v-time-picker format="24hr" scrollable ></v-time-picker>
            <v-spacer></v-spacer>
          </v-row>

        </v-card>
      </v-dialog>
    </v-row>
  </div>
</template>

<script>
 export default {
    data () {
      return {
        title:'',
        memo:'',
        dialog: false,
        dialog2: false,
        dialog3: false,
        notifications: false,
        sound: true,
        widgets: false,
        minPicker: (new Date(Date.now() - (new Date()).getTimezoneOffset() * 60000)).toISOString().substr(0, 10),
        picker: (new Date(Date.now() - (new Date()).getTimezoneOffset() * 60000)).toISOString().substr(0, 10),
        select: [
          { text: 'State 1' },
          { text: 'State 2' },
          { text: 'State 3' },
          { text: 'State 4' },
          { text: 'State 5' },
          { text: 'State 6' },
          { text: 'State 7' },
        ],
      }
    },
  }
</script>

<style>

</style>