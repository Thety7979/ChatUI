<template>
    <div class="flex items-center justify-center bg-gradient-to-r from-purple-400 via-pink-500 to-red-500 min-h-screen">
        <div class="bg-white relative rounded-none shadow-lg h-[90vh] flex overflow-visible"
            style="width: calc(100% - 10vh);">
            <div class="absolute top-0 right-0 mt-4 mr-4 flex items-center text-gray-500">
                <div class="relative">
                    <span @click="toggleDropdown" class="cursor-pointer">{{ currentStatus }}</span>
                    <i @click="toggleDropdown" class="fas fa-caret-down ml-4 cursor-pointer"></i>
                    <div v-if="dropdownOpen"
                        class="absolute right-0 mt-2 w-40 bg-white border border-gray-200 shadow-lg rounded z-50">
                        <ul>
                            <li v-for="option in statusOptions" :key="option" @click="selectStatus(option)"
                                class="px-4 py-2 hover:bg-gray-100 cursor-pointer">
                                {{ option }}
                            </li>
                        </ul>
                    </div>
                </div>
                <i class="fas fa-bell ml-4 cursor-pointer"></i>
            </div>
            <Sidebar />
            <ChatList />
            <ChatWindow class="flex-1" />
        </div>
    </div>
</template>

<script>
import Sidebar from "./Sidebar.vue";
import ChatList from "./ChatList.vue";
import ChatWindow from "./ChatWindow.vue";

export default {
    name: "ChatUI",
    components: {
        Sidebar,
        ChatList,
        ChatWindow
    },
    data() {
        return {
            dropdownOpen: false,
            statusOptions: ["Sale", "Rent", "Lease"],
            currentStatus: "Sale"
        };
    },
    methods: {
        toggleDropdown() {
            this.dropdownOpen = !this.dropdownOpen;
        },
        selectStatus(option) {
            this.currentStatus = option;
            this.dropdownOpen = false;
        }
    }
};
</script>