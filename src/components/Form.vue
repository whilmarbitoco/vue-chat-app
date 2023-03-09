<template>
    <form @submit.prevent="submit">
        <div class="input">
            <input
                v-model="chats.msg"
                type="text"
                name="text-data"
                id="text-data"
                placeholder="message"
            />
            <button type="submit">send</button>
        </div>
    </form>
</template>

<script>
export default {
    name: "Form",
    data() {
        return {
            chats: [],
        };
    },
    methods: {
        submit() {
            this.$emit('message-sent', this.chats);
            this.chats.msg = '';
        }
    }
};
</script>


<style>
.input {
    margin: 1rem;
    display: flex;
    padding: 10px;
    border-radius: 25px;
    background: rgba(255, 255, 255, 0.09);
    box-shadow: 0 4px 30px rgba(0, 0, 0, 0.1);
    backdrop-filter: blur(7.8px);
    -webkit-backdrop-filter: blur(7.8px);
    border: 1px solid rgba(255, 255, 255, 0.3);
}

input[type="text"] {
    display: block;
    margin-right: 2px;
    margin-left: 10px;
    width: 80%;
    padding: 0.375rem 0.75rem;
    font-size: 1rem;
    line-height: 1.5;
    color: #fff;
    background: var(--secondColor);
    background-clip: padding-box;
    border: none;
    border-bottom: 1px solid gray;
    transition: border-color 0.15s ease-in-out, box-shadow 0.15s ease-in-out;
}

input[type="text"]:focus {
    border-bottom: 1px solid #fff;
    outline: 0;
}

input:placeholder {
    color: #fff;
}

button {
    display: block;
    margin-right: 10px;
    margin-left: 2px;
    padding: 0.375rem 0.75rem;
    font-size: 1rem;
    line-height: 1.5;
    color: #fff;
    background: var(--secondColor);
    background-clip: padding-box;
    border: 1px solid #ced4da;
    border-radius: 0.25rem;
}

button:focus {
    color: #fff;
    background: var(--thirdColor);
    border-color: var(--thirdColor);
    outline: 0;
}
</style>
