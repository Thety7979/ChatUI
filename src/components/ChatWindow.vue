<template>
    <div class="w-2/4 p-4 flex flex-col" style="background-color: rgba(255,255,255,0.7);">
        <div class="mb-12">
            <div class="relative" style="transform: translateY(50px);">
                <h2 class="text-xl font-semibold">Gold Coast</h2>
                <p class="text-sm text-gray-500">From: Hali</p>
            </div>
        </div>
        <hr class="border-t border-gray-300 my-2" />
        <div class="flex-1 overflow-y-auto mt-2">
            <div v-for="message in messages" :key="message.id" class="mb-4">
                <div class="flex items-start mb-2">
                    <div class="flex flex-col items-center mr-3">
                        <div class="rounded-full p-1" style="background-color: #33B5FF;">
                            <img alt="Avatar Mikhar" class="rounded-full w-10 h-10" :src="avatar2" width="40"
                                height="40" />
                        </div>
                        <span class="text-xs text-gray-400 ml-2">{{ message.time }}</span>
                    </div>
                    <div>
                        <div class="bg-gray-300 text-gray-700 p-2 rounded-3xl">
                            <p class="text-sm">Welcome</p>
                        </div>
                    </div>
                </div>
                <div v-if="message.sender === 'me'" class="flex items-end justify-end">
                    <div class="bg-blue-500 text-white p-2 rounded-3xl">
                        <p class="text-sm">{{ message.content }}</p>
                    </div>
                    <span class="text-xs text-gray-400 ml-2">{{ message.time }}</span>
                </div>
            </div>
        </div>
        <div class="pt-4">
            <div class="flex mb-2">
                <button
                    class="bg-white text-gray-600 px-4 py-2 rounded-full mr-2 transform transition-transform duration-200 hover:scale-105 shadow-md">
                    REQUEST VISIT
                </button>
                <button
                    class="bg-white text-gray-600 px-4 py-2 rounded-full transform transition-transform duration-200 hover:scale-105 shadow-md">
                    MAKE OFFER
                </button>
            </div>

            <div class="relative">
                <i
                    class="fas fa-smile absolute left-3 top-1/2 transform -translate-y-1/2 text-gray-400 cursor-pointer"></i>
                <input v-model="newMessage" @keyup.enter="sendMessage"
                    class="w-full pl-10 pr-20 p-2 border border-gray-300 rounded-lg" placeholder="Type a message..."
                    type="text" />
                <div class="absolute right-3 top-1/2 transform -translate-y-1/2 flex items-center space-x-2">
                    <i class="fas fa-paperclip text-gray-400 cursor-pointer" @click="attachFile"></i>
                    <i class="fas fa-paper-plane cursor-pointer border border-blue-500 bg-blue-500 text-white rounded-full p-2 transition-transform duration-200 shadow-md hover:scale-110 hover:shadow-lg"
                        @click="sendMessage"></i>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import avatar1 from '../assets/images/avatar1.png';
import avatar2 from '../assets/images/avatar2.png';
import avatar3 from '../assets/images/avatar3.png';
import avatar4 from '../assets/images/avatar4.png';
import avatar5 from '../assets/images/avatar5.png';
import avatar6 from '../assets/images/avatar6.png';


export default {
    name: "ChatWindow",
    data() {
        return {
            avatar2,
            newMessage: "",
            messages: []
        };
    },
    mounted() {
        const savedMessages = localStorage.getItem("chatMessages");
        if (savedMessages) {
            this.messages = JSON.parse(savedMessages);
        }
    },
    methods: {
        sendMessage() {
            const content = this.newMessage.trim();
            if (!content) return;

            const message = {
                id: Date.now(),
                content,
                sender: "me",
                time: new Date().toLocaleTimeString([], { hour: "2-digit", minute: "2-digit" })
            };

            this.messages.push(message);
            localStorage.setItem("chatMessages", JSON.stringify(this.messages));
            this.newMessage = "";
        }
    }
};
</script>