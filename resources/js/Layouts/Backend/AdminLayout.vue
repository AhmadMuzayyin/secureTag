<script setup>
import Sidebar from '@/Components/Admin/Sidebar.vue'
import Header from '@/Components/Admin/Header.vue'
import Footer from '@/Components/Admin/Footer.vue'
import { ref, onMounted } from 'vue'

const openSidebar = ref(window.innerWidth >= 1024 ? true : false)
</script>

<template>
    <div class="bg-dashboard">
        <!-- Page Sidebar -->
        <Sidebar :open-sidebar="openSidebar" @closeSidebar="openSidebar = false"/>

        <div class="lg:ml-64 min-h-screen flex flex-col justify-between">
            <div class="px-4 md:px-8 pb-8">
                <!-- Page Header -->
                <Header @openSidebar="openSidebar = true"/>

                <!-- Page Content -->
                <main>
                    <slot />
                </main>
            </div>

            <!-- Page Footer -->
            <Footer/>
        </div>
    </div>
</template>
