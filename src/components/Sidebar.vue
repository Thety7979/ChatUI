<template>
    <div class="w-1/6 bg-gray-100 p-4">
        <div class="flex flex-col items-center my-6">
            <div class="bg-white p-2 rounded-full" style="width: 80px; height: 80px;">
                <img src="https://storage.googleapis.com/a1aa/image/zT-PHvhUlmqU3IsL7URQ0S3dEEOdrrLqefnN6VOVvig.jpg"
                    alt="Account Picture" class="rounded-full w-full h-full object-cover" />
            </div>
            <div class="flex items-center mt-2">
                <h2 class="text-lg font-semibold">Jimi Hendrix</h2>
                <i class="fas fa-chevron-down text-gray-500 ml-1 text-sm"></i>
            </div>
        </div>
        <nav>
            <ul class="space-y-6">
                <li v-for="item in menuItems" :key="item.name" @click="activeMenu = item.name"
                    :class="{ 'border-l-4 border-blue-500 text-blue-500 font-semibold': activeMenu === item.name }">
                    <a class="flex items-center pl-4 py-2 cursor-pointer hover:text-blue-500 transition-all">
                        <i :class="[item.icon, 'mr-4']"></i>
                        {{ item.label }}
                    </a>
                </li>
            </ul>
        </nav>
    </div>
</template>

<script>
export default {
    name: "Sidebar",
    data() {
        return {
            activeMenu: "Chat",
            menuItems: [
                { name: "Properties", label: "Properties", icon: "fas fa-home" },
                { name: "Chat", label: "Chat", icon: "fas fa-comments" },
                { name: "Calendar", label: "Calendar", icon: "fas fa-calendar-alt" },
                { name: "Offers", label: "Offers", icon: "fas fa-folder" },
                { name: "Documents", label: "Documents", icon: "fas fa-file-alt" },
                { name: "Settings", label: "Settings", icon: "fas fa-cog" }
            ]
        };
    }
};
</script>
