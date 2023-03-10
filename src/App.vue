<template>
    <div class="main">
        <Navbar />
        <Chats :chats="chats" :receive="receive" />
        <Form @message-sent="sendMessage" />
        <Footer />
    </div>
</template>

<script>
import Navbar from './components/Navbar.vue';
import Chats from './components/Chats.vue';
import Form from './components/Form.vue';
import Footer from './components/Footer.vue';
import { Configuration, OpenAIApi } from "openai";



  
export default {
    name: "App",
    components: {
        Navbar,
        Chats,
        Form,
        Footer
    },
    data() {
        return {
            chats: [],
            receive: [],
            state: false,
        };
    },
    methods: {

      async sendMessage(chats) {
  if (chats) {
    const newChat = {
      id: Math.floor((Math.random() * 19244727) / 10),
      msg: chats.msg,
    };
    this.chats.push(newChat);
    this.state = true;

    try {
      const apikey = "<your openai api key>";

      const configuration = new Configuration({
  apiKey: apikey
});
const openai = new OpenAIApi(configuration);
      const com = await openai.createCompletion({
    model: "text-davinci-003",
    prompt: chats.msg,
    max_tokens: 2048, 
    temperature: 0,
    top_p:1.0,
    frequency_penalty: 0.0,
    presence_penalty: 0.0
    
  });

    const newRes = {
      id: Math.floor((Math.random() * 19244727) / 10),
      msg: com.data.choices[0].text,
    };
    this.receive = [newRes, ...this.receive];
      
      
    } catch (err) {
      console.log(err);
    }
  }
}


    },
};
</script>
