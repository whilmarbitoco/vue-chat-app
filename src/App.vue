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
            receive: [{id:1, msg: "hello"}],
            state: false,
        };
    },
    methods: {
        sendMessage(chats) {
            
            if (chats) {
                const newChat = {
                    id: Math.floor((Math.random() * 19244727) / 10),
                    msg: chats.msg,
                };
                this.chats.push(newChat);
                this.state = true;
            }
        },
    },
};
</script>
