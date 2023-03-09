<template>
    <div class="chat">
        <div v-for="r in receive" :key="r.id" class="receive">
            <img class="r-img" src="img/julien.jpg" alt="yoyoy" />
            <p class="r-p">{{ r.msg }}</p>
        </div>

        <div v-for="chat in chats" :key="chat.id" class="response">
            <p class="e-p">{{ chat.msg }}</p>
            <img class="e-img" src="img/alison.jpg" alt="yoyoy" />
        </div>
    </div>
</template>

<script>
export default {
    name: "Chats",
    props: {
        receive: Array,
        chats: Array,
    },
};
</script>

<style>
.chat {
    height: 30rem;
    margin: 1rem;
    font-size: 13px;
    overflow: scroll;
    background: rgba(255, 255, 255, 0.09);
    border-radius: 16px;
    box-shadow: 0 4px 30px rgba(0, 0, 0, 0.1);
    backdrop-filter: blur(7.8px);
    -webkit-backdrop-filter: blur(7.8px);
    border: 1px solid rgba(255, 255, 255, 0.3);
}

.chat p {
    padding: 0.5em 1em;
    align-self: center;
    max-width: 20rem;
    text-overflow: auto;
    background: rgba(255, 255, 255, 0.09);
    border-radius: 16px;
    box-shadow: 0 4px 30px rgba(0, 0, 0, 0.1);
    backdrop-filter: blur(7.8px);
    -webkit-backdrop-filter: blur(7.8px);
    border: 1px solid rgba(255, 255, 255, 0.3);
}

.chat img {
    width: 3rem;
    height: 3rem;
    border-radius: 50%;
}

.receive {
    padding: 1rem;
    display: flex;
    width: 100%;
}

.receive img {
    margin-right: 1rem;
}

.response img {
    margin-left: 1rem;
}

.response {
    padding: 1rem;
    display: flex;
    justify-content: flex-end;
}
</style>
