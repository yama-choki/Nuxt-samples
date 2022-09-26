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
                        @click="dialog = false,addEvent()"
                    >
                        <v-icon>mdi-calendar-edit-outline</v-icon>
                    </v-btn>
                </v-card-actions>
            </v-toolbar>

            <v-card-text>
                <div class="text-h2 pa-4">
                    <v-container fluid>
                        <v-text-field
                            v-model="name"
                            counter="10"
                            hint="10文字以内"
                            label="タイトル"
                        ></v-text-field>
                        <v-row>
                          <v-col
                           cols="11"
                          >
                            <div style="pointer-events: none;">
                              <v-text-field
                                  v-model="start"
                                  label="開始"
                              ></v-text-field>
                            </div>
                          </v-col>
                          <v-col
                            cols="1"
                            class="pt-10"
                          >
                            <InputTime
                              :title ='startDialogTitle'
                              @inputStart="inputStart"
                            >
                            </InputTime>
                          </v-col>
                        </v-row>
                        <v-row>
                          <v-col
                           cols="11"
                          >
                            <div style="pointer-events: none;">
                              <v-text-field
                                  v-model="end"
                                  label="終了"
                              ></v-text-field>
                            </div>
                          </v-col>
                          <v-col
                            cols="1"
                            class="pt-10"
                          >
                            <InputTime
                              :title ='endDialogTitle'
                              @inputEnd="inputEnd"
                            >
                            </InputTime>
                          </v-col>
                        </v-row>
                        <button style="width: 100%;" @click="colorPick = !colorPick">
                          <div style="pointer-events: none;">
                            <v-text-field
                                v-model="color"
                                label="色"
                            ></v-text-field>
                          </div>
                        </button>
                        <v-fab-transition>
                          <v-row v-show="colorPick">
                            <v-card class="px-8">
                              <v-radio-group
                                v-model="color"
                                column
                              >
                              <v-row>

                                <v-radio
                                  label="red"
                                  color="red"
                                  value="red"
                                ></v-radio>
                                <v-radio
                                  label="pink"
                                  color="pink"
                                  value="pink"
                                ></v-radio>
                                <v-radio
                                  label="purple"
                                  color="purple"
                                  value="purple"
                                ></v-radio>
                                <v-radio
                                  label="indigo"
                                  color="indigo"
                                  value="indigo"
                                ></v-radio>
                                <v-radio
                                  label="cyan"
                                  color="cyan"
                                  value="cyan"
                                ></v-radio>
                                <v-radio
                                  label="teal"
                                  color="teal"
                                  value="teal"
                                ></v-radio>
                                <v-radio
                                  label="green"
                                  color="green"
                                  value="green"
                                ></v-radio>
                                <v-radio
                                  label="lime"
                                  color="lime"
                                  value="lime"
                                ></v-radio>
                                <v-radio
                                  label="yellow"
                                  color="yellow"
                                  value="yellow"
                                ></v-radio>
                                <v-radio
                                  label="orange"
                                  color="orange"
                                  value="orange"
                                ></v-radio>
                              </v-row>
                              </v-radio-group>
                            </v-card>
                          </v-row>
                        </v-fab-transition>
                        <v-textarea
                            clearable
                            clear-icon="mdi-close-circle"
                            label="メモ"
                            counter="200"
                            hint="200文字以内"
                            v-model="memo"
                        ></v-textarea>
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
        colorPick: false,

        name:'',
        start:'',
        end:'',
        color:'',
        memo:'',
        allDay: true,
      }
    },
    methods:{
      inputStart(startDateTime){
        this.start = startDateTime
      },
      inputEnd(endDateTime){
        this.end = endDateTime
      },
      addEvent(){
        const schedule = [this.name, this.start, this.end, this.color, this.memo]
        console.log(schedule)
        // this.$emit('addEvent', schedule)
        this.name = ''
        this.start = ''
        this.end = ''
        this.color = ''
        this.memo = ''
      }
    }
  }
</script>

<style>
.v-enter-active, .v-leave-active {
  transition: all 500ms;
}

/* 表示アニメーション開始時 ・ 非表示アニメーション後 */
.v-enter, .v-leave-to {
  opacity: 0;
  transform: translateY(200px);
}
.v-leave-to {
  opacity: 0;
  transform: translateY(-200px);
}


</style>