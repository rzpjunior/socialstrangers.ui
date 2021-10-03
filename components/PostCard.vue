<template>
    <div>
        <v-card class="post-card">
            <v-card-title>
                Name, what's on your mind?
            </v-card-title>
            <v-card-text>
                <v-col>
                    <div class="d-flex flex-row align-center">
                        <v-text-field v-model="msg" placeholder="Type Something" counter maxlength="100" @keypress.enter="sendPost"></v-text-field>
                        <v-btn icon class="ml-4" @click="sendPost"><v-icon>mdi-send</v-icon></v-btn>
                    </div>
                </v-col>
            </v-card-text>
        </v-card>
        
        <!-- POST FEED -->
        <div class="post-feed" v-for="(item, idx) in arrPost.slice().reverse()" :key="idx">
            <v-card
                class="mx-auto"
                color="#236168"
                dark
                max-width="600"
            >
                <v-card-title>
                    <span class="date-post-card">
                        {{item.createdAt}}
                    </span>
                </v-card-title>

                <v-card-text class="text-h5 font-weight-bold">
                    {{item.message}}
                </v-card-text>

                <v-card-actions>
                <v-list-item class="grow">
                    <v-list-item-avatar color="grey darken-3">
                    <v-img
                        class="elevation-6"
                        alt=""
                        src="https://avataaars.io/?avatarStyle=Transparent&topType=ShortHairShortCurly&accessoriesType=Prescription02&hairColor=Black&facialHairType=Blank&clotheType=Hoodie&clotheColor=White&eyeType=Default&eyebrowType=DefaultNatural&mouthType=Default&skinColor=Light"
                    ></v-img>
                    </v-list-item-avatar>

                    <v-list-item-content>
                        <v-list-item-title>Your Name, 22</v-list-item-title>
                    </v-list-item-content>

                    <v-row
                        align="center"
                        justify="end"
                        >
                            <v-icon class="mr-1">
                                mdi-heart
                            </v-icon>
                            <span class="subheading mr-2">256</span>
                            <span class="mr-1">·</span>
                            <v-icon class="mr-1">
                                mdi-share-variant
                            </v-icon>
                        <span class="subheading">45</span>
                    </v-row>
                </v-list-item>
                </v-card-actions>
            </v-card>
        </div>
    </div>
</template>
<style scoped>
    .post-feed{
        margin-top:20px;
    }
    .date-post-card{
        font-size:12px;
    }
</style>
<script>
export default {
  data () {
    return {
      arrPost : [],
      msg: '',
    }
  },
  methods: {
      sendPost(){
            const today = new Date();
            const year = today.getFullYear();
            const month = today.toLocaleString('default', {month: 'long'});
            const date = month + ' ' + year

            const time = today.getHours() + ":" + today.getMinutes();
            const dateTime = date +', '+ time;

            let r = (Math.random() + 1).toString(36).substring(7);
            this.arrPost.push(
                {
                    postId: r,
                    message: this.msg,
                    createdAt: dateTime
                }
            )
            this.msg = ''
        },

  }
}
</script>