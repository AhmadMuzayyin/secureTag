<script setup>
import AdminLayout from '@/Layouts/Backend/AdminLayout.vue';
import ButtonCreate from '@/Components/Admin/ButtonCreate.vue';
import TableAction from '@/Components/Admin/TableAction.vue';
import ActionIcon from '@/Components/Admin/ActionIcon.vue';
import Pagination from '@/Components/Pagination.vue';
import { Head, Link } from '@inertiajs/inertia-vue3';

const props = defineProps({
    partners: Array
})
</script>

<template>
    <Head title="Data Partner" />

    <AdminLayout>
        <div class="card-dashboard">
            <div class="flex items-center justify-between mb-10">
                <h2 class="card-title-dashboard mb-0">Data Partner</h2>
                <ButtonCreate href="/panel/partner/create" />
            </div>
            <div class="flex flex-wrap items-center md:justify-between mb-5">
                <div class="flex items-center space-x-2 mb-2 md:mb-0">
                    <div>Show</div>
                    <select class="form-input-dashboard w-20">
                        <option value="10">10</option>
                        <option value="25">25</option>
                        <option value="50">50</option>
                        <option value="100">100</option>
                    </select>
                    <div>entries</div>
                </div>
                <div class="w-full md:w-auto">
                    <input
                        type="text"
                        class="form-input-dashboard"
                        placeholder="Search"
                    />
                </div>
            </div>
            <div class="w-full overflow-x-auto">
                <table class="table">
                    <thead>
                        <tr>
                            <th class="table-th">No</th>
                            <th class="table-th">Nama</th>
                            <th class="table-th">Email</th>
                            <th class="table-th">Pic</th>
                            <th class="table-th">Alamat</th>
                            <th class="table-th">Action</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr v-for="partner,index in partners.data" :key="partner.id">
                            <td
                                class="table-td"
                                :class="{ 'table-td-dark': partner.id % 2 != 0 }"
                            >
                                {{ ++index }}
                            </td>
                            <td
                                class="table-td"
                                :class="{ 'table-td-dark': partner.id % 2 != 0 }"
                            >
                                {{ partner.user.name }}
                            </td>
                            <td
                                class="table-td"
                                :class="{ 'table-td-dark': partner.id % 2 != 0 }"
                            >
                                {{ partner.user.email }}
                            </td>
                            <td
                                class="table-td"
                                :class="{ 'table-td-dark': partner.id % 2 != 0 }"
                            >
                                {{ partner.pic }}
                            </td>
                            <td
                                class="table-td"
                                :class="{ 'table-td-dark': partner.id % 2 != 0 }"
                            >
                                {{ partner.address }}
                            </td>
                            <td
                                class="table-td"
                                :class="{ 'table-td-dark': partner.id % 2 != 0 }"
                            >
                                <TableAction
                                    :detailHref="route('admin.partner.show',partner.user_id)"
                                    :editHref="route('admin.partner.edit',partner.user_id)"
                                    :deleteHref="route('admin.partner.destroy',partner.user_id)"
                                >
                                    <Link :href="route('admin.partner.list',partner.user_id)">
                                        <ActionIcon>
                                            <path
                                                stroke-linecap="round"
                                                stroke-linejoin="round"
                                                d="M3.75 12h16.5m-16.5 3.75h16.5M3.75 19.5h16.5M5.625 4.5h12.75a1.875 1.875 0 010 3.75H5.625a1.875 1.875 0 010-3.75z"
                                            />
                                        </ActionIcon>
                                    </Link>
                                </TableAction>
                            </td>
                        </tr>
                    </tbody>
                </table>
            </div>
            <Pagination :links="partners.links"/>
        </div>
    </AdminLayout>
</template>
