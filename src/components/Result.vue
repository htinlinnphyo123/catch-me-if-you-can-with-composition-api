<template>

    <div v-if="result">
        Your result is - {{ result }}
        <div v-if="result<=200">
            You are awesome.Best Player.
        </div>
        <div v-else-if="result<=400">
            Medium player.Keep going.
        </div>
        <div v-else>
            Nice try.YOu need to try more.Not bad.
        </div>
    </div>

</template>

<script>
export default {
    props : ['result']
}
</script>

<style>

</style>