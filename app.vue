<script setup>
const client = useSupabaseClient();

let { data: tournaments } = await useAsyncData("tournaments", async () => {
    const { data } = await client
        .from("LeagueTournaments")
        .select("tournament_name, start_date");

    return data;
});
</script>
<template>
    <div v-for="tournament in tournaments">
        {{ tournament.tournament_name }}
        {{ tournament.start_date }}
    </div>
</template>
