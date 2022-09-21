<template>
    <v-dialog
        transition="dialog-top-transition"
        max-width="600"
    >
        <template v-slot:activator="{ on, attrs }">
            <v-btn
                icon
                color="primary"
                v-bind="attrs"
                v-on="on"
            >
                <v-icon>mdi-pencil</v-icon>
            </v-btn>
        </template>
        <template v-slot:default="dialog">
            <v-card>
                <v-toolbar
                    color="primary"
                    dark
                >
                <v-card-actions class="justify-start">
                    <v-btn
                    text
                    @click="dialog.value = false"
                    >キャンセル</v-btn>
                </v-card-actions>
                <v-spacer></v-spacer>
                <v-card-title>
                    新しい予定
                </v-card-title>
                <v-spacer></v-spacer>
                <v-card-actions class="justify-end">
                    <v-btn
                    text
                    @click="dialog.value = false"
                    >保存</v-btn>
                </v-card-actions>
                </v-toolbar>
                <v-card-text>
                    <div class="text-h2 pa-12">
                        <v-container fluid>
                            <v-text-field
                                v-model="title"
                                :rules="rules"
                                counter="10"
                                hint="This field uses counter prop"
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
                            ></v-textarea>
                        </v-container>
                    </div>
                </v-card-text>
            </v-card>
        </template>
    </v-dialog>
</template>

<script>
export default {

}
</script>

<style>

</style>