<template>
    <div class="w-1/4 border-r border-gray-200 p-4 overflow-y-auto" style="background-color: rgba(255,255,255,0.7);">
        <h2 class="text-xl font-semibold">Chat</h2>

        <div class="mb-7 relative" style="transform: translateY(20px);">
            <div class="relative mt-2">
                <input class="w-full p-2 border border-gray-300 rounded-lg" placeholder="Search" type="text" />
                <i class="fas fa-search absolute right-3 top-3 text-gray-400"></i>
            </div>
        </div>
        <hr class="border-t border-gray-300 my-2" />
        <ul>
            <li v-for="chat in chats" :key="chat.id" class="mb-4">
                <a class="flex items-center p-2 border border-gray-300 rounded-none hover:bg-gray-50 transform transition-transform duration-200 hover:scale-105"
                    href="#">
                    <div class="rounded-full p-1 mr-3" :style="{ backgroundColor: chat.bgColor }">
                        <img :alt="'Avatar ' + chat.name" class="rounded-full w-10 h-10" :src="chat.avatar" width="40"
                            height="40" />
                    </div>
                    <div class="flex-1 relative">
                        <h3 class="font-semibold">{{ chat.name }}</h3>
                        <p class="text-sm text-gray-500">{{ chat.lastMessage }}</p>
                        <div class="absolute top-0 right-0 text-[10px] text-gray-500">
                            <div>{{ chat.date }}</div>
                            <div v-if="chat.unread > 0"
                                class="mt-1 text-center bg-red-500 text-white rounded-full px-1 py-[1px]">
                                {{ chat.unread }}
                            </div>
                        </div>
                    </div>
                </a>
            </li>
        </ul>
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
    name: "ChatList",
    data() {
        return {
            chats: [
                { id: 1, name: "Hurin Omar", lastMessage: "Sure 8pm", date: "02 Feb", unread: 3, avatar: avatar1, bgColor: "#FF5733" },
                { id: 2, name: "Hali", lastMessage: "early prototype of product", date: "02 Feb", unread: 1, avatar: avatar2, bgColor: "#33B5FF" },
                { id: 3, name: "Alice Nguyen", lastMessage: "Let's meet tomorrow", date: "03 Feb", unread: 0, avatar: avatar3, bgColor: "#FF33A8" },
                { id: 4, name: "Bob Tran", lastMessage: "Check out the new design", date: "03 Feb", unread: 5, avatar: avatar4, bgColor: "#33FF77" },
                { id: 5, name: "Carol Lee", lastMessage: "What's up", date: "04 Feb", unread: 0, avatar: avatar5, bgColor: "#FFBD33" },
                { id: 6, name: "David Kim", lastMessage: "Hey", date: "04 Feb", unread: 0, avatar: avatar6, bgColor: "#8E44AD" }
            ]
        };
    }
};
</script>