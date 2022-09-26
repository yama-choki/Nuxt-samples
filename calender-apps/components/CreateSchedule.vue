<template>
  <div>
    <v-row
      justify="center"
    >
      <v-btn
        color="primary"
        class="ma-2"
        icon
        @click="dialog = true"
      >
        <v-icon>mdi-pencil-plus</v-icon>
      </v-btn>

      <v-dialog
        v-model="dialog"
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
                        @click="dialog = false"
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
                        @click="dialog = false"
                    >
                        <v-icon>mdi-calendar-edit-outline</v-icon>
                    </v-btn>
                </v-card-actions>
            </v-toolbar>

            <v-card-text>
                <div class="text-h2 pa-12">
                    <v-container fluid>
                        <v-text-field
                            v-model="name"
                            counter="10"
                            hint="10文字以内"
                            label="タイトル"
                        ></v-text-field>
                        <div style="pointer-events: none;">
                          <v-text-field
                              v-model="start"
                              label="開始"
                          ></v-text-field>
                        </div>
                        <InputTime
                          :title ='startDialogTitle'
                          @inputStart="inputStart"
                        >
                        </InputTime>
                        <div style="pointer-events: none;">
                          <v-text-field
                              v-model="end"
                              label="終了"
                          ></v-text-field>
                        </div>
                        <InputTime
                          :title ='endDialogTitle'
                          @inputEnd="inputEnd"
                        >
                        </InputTime>
                        <v-textarea
                            clearable
                            clear-icon="mdi-close-circle"
                            label="メモ"
                            counter="200"
                            hint="200文字以内"
                            v-model="memo"
                        ></v-textarea>
                        <v-select
                        :items="color"
                        label="色"
                        item-value="text"
                        ></v-select>
                    </v-container>
                </div>
            </v-card-text>
          <v-card-text>
          </v-card-text>
        </v-card>
      </v-dialog>

      <!-- 3つ目のダイアログ　日時入力フォーム -->
    </v-row>
  </div>
</template>

<script>
import InputTime from './InputTime.vue'
 export default {
  components: { InputTime },
    data () {
      return {
        dialog: false,
        startDialogTitle:'開始日時',
        endDialogTitle:'終了日時',
        name:'',
        start:'',
        end:'',
        memo:'',
        color: [
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
    methods:{
      inputStart(startDateTime){
        this.start = startDateTime
      },
      inputEnd(endDateTime){
        this.end = endDateTime
      },
    }
  }
</script>

<style>

</style>