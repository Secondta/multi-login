<template>
    <div class="all text-center">
        <button v-if="userRole === 'admin'">Admin</button>
        <button v-if="userRole === 'guru'">Guru</button>
        <button v-if="userRole === 'siswa'">Siswa</button>
    </div>
</template>

<script>
export default {
    name: "link",
    computed: {
        userRole() {
            return JSON.parse(sessionStorage.getItem("USER_DATA")).role;
        }
    }
}
</script>